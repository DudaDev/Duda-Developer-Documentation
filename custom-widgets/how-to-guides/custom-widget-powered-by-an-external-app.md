# Custom Widget Powered by an External App

Many times it's necessary to use JavaScript code that must be hosted outside of Duda. It might be an existing widget that is used on platforms beyond Duda, or the development team would rather keep using their own integrated development environment (IDE) and deployment setup, instead of developing within the Duda Widget Builder. In scenarios like these, external applications can provide the flexibility needed to integrate complex external code with Duda.

### Objectives and Outcomes

In this tutorial you will learn how to use an external JavaScript application within a Duda website. The application will be hosted externally from Duda, but will render within both the live site and the editor. Additionally, site authors will be able to configure the application in the same way they can configure a native Duda widget.

We are going to create a simple JavaScript application that can be used to display a chart of data on a Duda website. It is possible to create a similar experience by adding the JavaScript directly to developer mode within the editor, but creating a custom widget provides more flexibility for the site author and the external application provides a better experience for the developer.

### Prerequisites

* Basic knowledge of JavaScript
* Knowledge of custom widgets and a plan with access to widget builder
* A hosting environment for the external application (S3 can work if necessary)
* An existing Duda site to place the custom widget in

### 1. Create the External Application

External applications are JavaScript files that are hosted outside of Duda. Using a method from the Partner JS API, you can pass information from the editor to the JavaScript, thereby enabling configuration indistinguishable from native Duda widgets. You will use the [Highcharts](https://www.highcharts.com/) JS library to render a chart based on sample JSON. In a production application the JSON would likely come straight from an API endpoint, but for our example we'll be using static data. The actual JavaScript application is a simple function that configures a Highcharts instance for display.

{% tabs %}
{% tab title="Drawchart function" %}
```javascript
function drawChart(container) {
  Highcharts.chart(container, {
    chart: {
      type: 'bar'
    },
    title: {
      text: 'Fruit Consumption'
    },
    xAxis: {
      categories: ['Apples', 'Bananas', 'Oranges']
    },
    yAxis: {
      title: {
        text: 'Fruit eaten'
      }
    },
    series: [{
      name: 'Jane',
      data: [1, 0, 4]
    },{
      name: 'John',
      data: [5, 7, 3]
    }]
  });
}
```
{% endtab %}
{% endtabs %}

Calling the **drawChart** function configures and renders a simple bar chart into the element passed to the function. To make this application work with a Duda custom widget, you need to add an initialization and cleanup method that Duda can execute at the appropriate time of page load and unload.

{% tabs %}
{% tab title="Initialization and cleanup" %}
```javascript
var handler = {
  // these methods must be named init and clean

  init: function(options){
    dmAPI.loadScript('https://code.highcharts.com/highcharts.js').then(function(){
      drawChart(options.container);
    });
  },

  clean: function(options) {
    options.container.innerHTML = '';
  }
}

dmAPI.registerExternalWidget('chart', handler)
```
{% endtab %}
{% endtabs %}

You’ve added an object with two methods named init and clean. These methods are required by the widget builder as entry and exit points into your external application. Both methods receive an **options** object that contains the container that the widget will be rendered into. Our init script uses the Partner JS API method loadScript to load Highcharts dependency and then calls the **drawChart** method, passing the container to the function. The clean method erases the content of the container before the page is unloaded by setting the innerHTML property to a blank string. Use an additional Partner JS API method to register your widget with an identifier, passing in the object you just created. You will reference this identifier later in the widget builder.

Upload the JavaScript file to your hosting environment, or you can use [this one hosted on S3](https://se-duda.s3.us-east-2.amazonaws.com/external-applications/chart-step-1.js).

### 2. Create a Custom Widget

In your Duda account, select the **Team** tab and then **Widget Builder**. Once the Widget Builder dashboard is loaded, click **Create New Widget**. Name your widget using the text field in the new widget modal, and then click **Create**. The Widget Builder UI will load with an empty HTML editor. Select **JavaScript** in the sidebar. You'll see an empty function in the JavaScript editor with three arguments: **element**, **data** and **api**.

To embed the external application in your custom widget, use the **renderExternalApp** method located on the api object passed to the function. The renderExternalApp method takes 4 parameters: script source, the element that the external app will be rendered into that is passed to both the init and clean methods, a configuration object to be passed to the init function, and an options object.

{% tabs %}
{% tab title="Custom widget code" %}
```javascript
api.scripts.renderExternalApp(<scriptSrc>, element, {}, { amd: false, name: 'chart' });
```
{% endtab %}
{% endtabs %}

NOTE: You may use the [URL of our hosted file](https://se-duda.s3.us-east-2.amazonaws.com/external-applications/chart-step-1.js) as the scriptSrc in your testing.

When working with vanilla JavaScript, you set the **amd** property to false within the options object. Additionally, pass the same identifier you used with the registerExternalWidget method as the value for the **name** property.

The **element** is usually passed through straight from the main function within the JavaScript editor, however there may be certain cases where you want to pass a different DOM reference.\
The **scriptSrc** parameter should be the URL of your hosted JavaScript file.

Click **Save** and then **Publish** to make your new widget available for installation on your sites.

### 3. Add the Widget to a Site

Return to your dashboard and select an existing site, or create a new site to test the widget. Select the **Widgets** tab from the editor sidebar, then locate or search for the name you entered in the widget builder when creating the custom widget. Drag the widget onto your site and you should see a simple bar chart render. Because of our **init** entry method, Duda can correctly render the widget within the editor or on the live site even though the JavaScript file is located elsewhere.

### 4. Allow the Widget to Be Configured from the Editor

While simple, option-free widgets may be useful in certain circumstances, the ability to configure an external app through the widget's content panel is a powerful feature allowing site authors to customize your widget without reading or modifying code. Allowing configuration of an external application consists of three parts: the UI to allow the author to update the configuration, capturing the configuration in the custom widget and sending it to the external application, and using the configuration values within the external application code.

**4.1 Create a Configuration UI**

Navigate back to the widget builder by selecting **Team** then **Widget Builder** from the site dashboard header. Find your widget in the widget dashboard and click the **Edit** link. In the sidebar, select **Content Editor**. The content editor allows you to build your own UI for the content panel that appears in the editor when you click on a widget that has been added to a site.

You’re going to create a simple configuration that allows you to change the title of the chart. At the bottom of the Content Editor, click the **Add Input** link. In the **Input configuration** column, select **Text** from the **Input Type** dropdown. In the form that appears, enter _title_ in the **Variable** field and _Title_ (capitalized) in the **Descriptive label** field. Keep the rest of the fields blank.

**4.2 Capture the Widget Configuration within the Custom Widget**

Switch back to the **JavaScript** editor panel where you entered the renderExternalApp method. You’re going to update the method to pass the contents of the title field you created in the content editor to the external application. The values the author enters in the content panel appear as properties on the data argument found in the main widget function, making it simple to forward on the values.

{% tabs %}
{% tab title="Widget configuration" %}
```javascript
// passing along the contents of the 'title' field to the external application.
// The data.config option contains the values of all the fields created
// in the content editor.

api.scripts.renderExternalApp(<scriptSrc>, element, { title: data.config.title }, { amd: false, name: 'chart' });
```
{% endtab %}
{% endtabs %}

To access the title the site author entered, use the variable name of the field. If you followed the instructions above, the variable should be named _title_. Retrieve the value by using the variable name as a property name on the **data.config** object. You can specify a new property on the third argument of the renderExternalApp function to be sent as additional data to the init function of your external application.

Click **Save** and then **Republish** in the header of the Widget Builder. In the republish modal enable the **Auto update widget on all sites** toggle to automatically update the existing widget you used on your test site.

**4.3 Use the Configuration Within the External Application**

The final step is to use the values within your external application. This requires two small changes to your code. First, update the call to drawChart in your init method to pass along the configuration. Then in your function use the value of the title property as the content for the chart title.

Your init function passed an options object as an argument, which you used to obtain a reference to the DOM element that the chart should be rendered into. You can get additional information by accessing the _props_ property on the same object. Your updated init function should look like this:

{% tabs %}
{% tab title="Configuration" %}
```javascript
init: function(options){
  dmAPI.loadScript('https://code.highcharts.com/highcharts.js').then(function(){
    // Any configuration passed from the custom widget will be available on the 
    // options.props property. We pass along all the configuration to our drawChart
    // function.

    drawChart(options.container, options.props);
  });
}
```
{% endtab %}
{% endtabs %}

Your drawChart function can now be updated to use the _title_ property in the Highcharts configuration. You also provide a default title in case no title was entered into the content panel within the editor.

{% tabs %}
{% tab title="Using duda config" %}
```javascript
function drawChart(container, props) {
  Highcharts.chart(container, {
    chart: {
      type: 'bar'
    },
    title: {
      text: props.title || 'Fruit Consumption'
    },
    …
  })
}
```
{% endtab %}
{% endtabs %}

Save the updated JavaScript file and upload it to your hosting environment. Alternatively, you can use [this hosted file](https://se-duda.s3.us-east-2.amazonaws.com/external-applications/chart-step-2.js). Return to your testing site, and select the previously added chart widget. The content panel will now display a text field for entering a title.

Changing the configuration within the content panel will automatically rerender the external application, giving the site author instant feedback for their edits.
