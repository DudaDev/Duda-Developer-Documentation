# Profile Guidelines

The manifest's `app_profile` object holds the information that affects the text and images of the App Card and the App Profile.

<figure><img src="https://files.readme.io/489699a-Untitled.png" alt="1858"><figcaption><p>App Card Overview</p></figcaption></figure>

<figure><img src="https://files.readme.io/78bb657-Untitled1.png" alt="2584"><figcaption><p>App Profile Overview</p></figcaption></figure>

### App Name

The name of your app plays a critical role in how users perceive it in the App Store. Choose a name that is relevant, memorable, and hints at what your app does. Avoid generic names or ones that are too similar to name of already existing apps. We also recommend limiting your app name to no more than 25 characters.

### App Logo

The app logo icon should be a 500 x 500 px square, saved in preferably SVG, or WebP format (though PNG or JPEG are also supported).

### Short Description

The short description is a subtitle and is intended to provide a brief overview of your app's capabilities or offering.

When writing a short description you should align with the following guidelines:

* **Keep it short**. A short description should be between 55-105 characters long.
* **Keep it simple**. Assume users are not familiar with your industry specific jargon. Use plain words to explain what the app does and why they should add it.
* **Keep it precise**. Avoid using superlatives ("best app in the world") or providing information that is not related to what the app does.

### Long Description

Divide your long description to two main areas, Key Features and Full Description.

* **Key Benefits**. Provide 3-5 bullet points highlighting the main benefits of your app. As users tend to focus on these key benefits alone, this is your chance to grab your potential user's attention and promote your app. When listing the key features, limit yourself to 500 characters.
* **Full Description**. This description is provided below the key features section and is aimed to further communicate your app's value proposition and should be thorough and address important aspects of your app. The rule of three also applies here, hence the ideal description consists of three concise and informative paragraphs (though this is not a strict requirement).

When writing the full description you should align with the following guidelines:

* The full descriptions should be no more than 1500 characters long.
* Each section in the full description should be structured in the following manner: (A) Section Heading, (B) Section Text and (optional) (C) Section Bullets. As a best practice, you should limit the length of each section to no more than 300 characters.

The description is rendered in the App Store as an HTML markup. Therefore, when providing your app description in the manifest (within the `app_long_description` property) you should use the following template:

{% tabs %}
{% tab title="HTML" %}
```html
<div
    style='font-family: Source Sans Pro; font-size: 15px; font-weight: normal; font-stretch: normal ;font-style: normal ;line-height: 1.69; letter-spacing: normal; color: #2f373a;'>
    <h2>Key Benefits</h2>
    <ul style='padding-left:20px'>
        <li>{PROVIDE LIST OF KEY FEATURES HERE}</li>
    </ul>
    <h3 style='padding-top:20px'>{SECTION TITLE}</h3>
    <p> {APP FULL DESCRIPTION GOES HERE} </p>
</div>
```
{% endtab %}
{% endtabs %}

This example further shows how the serve the long description within the Manifest:

{% tabs %}
{% tab title="HTML" %}
```html
<div
    style='font-family: Source Sans Pro;font-size: 15px;font-weight: normal;font-stretch: normal;font-style: normal;line-height: 1.69;letter-spacing: normal;color: #2f373a;'>
    <h2>Key Benefits</h2>
    <ul style='padding-left: 20px;'>
        <li>Can sometimes kiil your cat, but not your dog</li>
        <li>Probably does not omit radiation</li>
        <li>Personalized customer experience: Window pop-ups with single match caller details to understand the purpose
            of the call before even connecting</li>
    </ul>
    <h3 style='padding-top: 20px'>Our Best Feature</h3>
    <p>Meggings hammock jianbing cray single-origin coffee church-key, cred typewriter. Pinterest iceland tilde 90's man
        bun, poutine fam waistcoat mustache readymade pabst cray actually skateboard. Meggings hammock jianbing cray
        single-origin coffee church-key, cred typewriter. </p>
    <h3 style='padding-top: 20px'>Our Worst Feature</h3>
    <p> Why use post when this sofa is here disappear for four days and return home with an expensive injury; bite the
        vet. Intrigued by the shower drool sit in window and stare oooh, a bird, yum or i want to go outside let me go
        outside nevermind inside is better purrr purr littel cat. Snuggles up to shoulders or knees and purrs you to
        sleep the dog smells bad cat fur is the new black or always hungry.</p>
    <h3 style='padding-top: 20px'>Hey Look! A Bird!</h3>
    <p>Glossier man bun green juice tofu viral hella disrupt DIY man braid flexitarian affogato godard. Hammock fixie
        pug messenger bag. Retro hella 8-bit, adaptogen XOXO freegan before they sold out lomo tote bag mustache
        leggings man braid kickstarter. Meggings hammock jianbing cray single-origin coffee church-key, cred typewriter.
    </p>
    <div>
```
{% endtab %}
{% endtabs %}

Using this markup will yield the following app description:

<figure><img src="https://files.readme.io/f2380c9-Untitled2.png" alt=""><figcaption></figcaption></figure>

### App Images

Visually communicate your app with 3-6 images of 1,278 x 948 (4:3 aspect ratio), saved in preferably SVG, or WebP format (though PNG or JPEG are also supported).

Focus each image on a main benefit or feature so that you fully convey your app’s value.

Images should not be mere screenshots of your app, but should rather be relevant and accurately represent your app. You may include small amount of text on your image to further explain what your app does, what its features are, or what problem is it solving.

In addition, please\* follow these guidelines:

* All images showcasing the app functionality should do so integrated into the Duda editor (for example, an app that uses a widget or dashboard should show it within the Duda editor).
* To the extent possible, provide images of how the app would look like in an user website, both in desktop and mobile versions.
* Don't use real user data; showcase anonymized or fictional data instead.
