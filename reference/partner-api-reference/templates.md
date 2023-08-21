# Templates

## Template Object

{% tabs %}
{% tab title="JSON" %}
```json
{
    "template_name": "Consultant Landing Page",
    "preview_url": "http://dashboard.russjeffery.com/preview/dm-theme-1026287-en-343",
    "thumbnail_url": "https://irp-cdn.multiscreensite.com/c1e7738d32ae46538527c1fd4e95a9b9/siteTemplateIcons/4CXbg61CTvKDPTEyC7EQ_Consultant_landing_page_3%20screens.png",
    "desktop_thumbnail_url": "https://irp-cdn.multiscreensite.com/c1e7738d32ae46538527c1fd4e95a9b9/siteTemplateIcons/jASytIEDRJWRG0dxSbJj_Consultant_landing_page_Desktop.png",
    "tablet_thumbnail_url": "https://irp-cdn.multiscreensite.com/c1e7738d32ae46538527c1fd4e95a9b9/siteTemplateIcons/4XZxi7HCTWaPx7oTc6fW_Consultant_landing_page_Tablet.png",
    "mobile_thumbnail_url": "https://irp-cdn.multiscreensite.com/c1e7738d32ae46538527c1fd4e95a9b9/siteTemplateIcons/8V63M24zRYaJG96sWSdu_Consultant_landing_page_Mobile.png",
    "template_id": 1026287,
    "template_properties": {
        "can_build_from_url": false,
        "has_store": false,
        "has_blog": false,
        "page_count": 1,
        "type": "duda"
    }
}
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th width="270">Property</th><th>Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>template_name</strong></td><td><em>string</em></td><td>The name of the template.</td></tr><tr><td><strong>preview_url</strong></td><td><em>string</em></td><td>A direct URL to preview the template. This URL is publicly available and does not require authentication.</td></tr><tr><td><strong>thumbnail_url</strong></td><td><em>string</em></td><td>A direct URL to a JPG image displaying the template. This would be good to use to show in a template selection page.</td></tr><tr><td><strong>mobile_thumbnail_url</strong></td><td><em>string</em></td><td>A screenshot of the mobile view of this template.</td></tr><tr><td><strong>desktop_thumbnail_url</strong></td><td><em>string</em></td><td>A screenshot of the desktop view of this template.</td></tr><tr><td><strong>tablet_thumbnail_url</strong></td><td><em>string</em></td><td>A screenshot of the tablet view of this template.</td></tr><tr><td><strong>template_id</strong></td><td><em>number</em></td><td>A unique number associated with this template. This is used to create the template from.</td></tr><tr><td><strong>template_properties</strong></td><td><em>object</em></td><td>Contains proprieties of the templates. See details below</td></tr></tbody></table>

#### Template Properties Object

<table><thead><tr><th width="269">Property</th><th width="223">Type</th><th width="255">Description</th></tr></thead><tbody><tr><td><strong>has_store</strong></td><td><em>bool</em></td><td>If the template has an eCommerce store built into it.</td></tr><tr><td><strong>has_blog</strong></td><td><em>bool</em></td><td>If the template has a blog added to the website once it's created.</td></tr><tr><td><strong>page_count</strong></td><td><em>number</em></td><td>The number of pages this template contains.</td></tr><tr><td><strong>can_build_from_url</strong></td><td><em>bool</em></td><td>If the template can be built from a URL</td></tr><tr><td><strong>type</strong></td><td><em>string</em></td><td>One of 'duda' or 'custom'. Specifies if a template is a native Duda template or a custom template built by the organization.</td></tr></tbody></table>

{% hint style="info" %}
**Good to Know: Only templates built by Duda will have a tablet or mobile screenshot returned in the API**

Duda does not currently have a way to generate mobile & tablet preview screenshots for custom templates.
{% endhint %}

## List Templates

{% swagger method="get" baseUrl="https://api.duda.co/api" expanded="false" fullWidth="false" summary="List Templates" path="/sites/multiscreen/templates" %}
{% swagger-description %}
Get all available Templates.
{% endswagger-description %}

{% swagger-parameter in="query" name="lang" type="string" %}
Retrieve templates for specific languages.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="array of objects" %}
```json
[
  {
    "template_name": "Auto Repair",
    "preview_url": "http://dashboard.russjeffery.com/preview/dm-theme-1005442-en-328",
    "thumbnail_url": "https://irp-cdn.multiscreensite.com/0f8a84df3a244e0f9249423e0588397f/siteTemplateIcons/IzrGRlYSCeQNUc4V1nAA_Auto_repair_BigPreview.png",
    "desktop_thumbnail_url": "https://irp-cdn.multiscreensite.com/0f8a84df3a244e0f9249423e0588397f/siteTemplateIcons/GwrdUIcXTbOypxHaiUNZ_auto_repair_desktop.png",
    "tablet_thumbnail_url": "https://irp-cdn.multiscreensite.com/0f8a84df3a244e0f9249423e0588397f/siteTemplateIcons/LUihe1rSq5kiizBraMgG_auto-repair_ipad.png",
    "mobile_thumbnail_url": "https://irp-cdn.multiscreensite.com/0f8a84df3a244e0f9249423e0588397f/siteTemplateIcons/rcceNsKOTKSqSx5bnPME_auto-repair-mobile.png",
    "template_id": 1005442,
    "template_properties": {
      "can_build_from_url": false,
      "has_store": false,
      "has_blog": false,
      "page_count": 5,
      "type": "duda"
    }
  },
  {
    "template_name": "Blank Services",
    "preview_url": "http://dashboard.russjeffery.com/preview/dm-theme-1003738-en-327",
    "thumbnail_url": "https://irp-cdn.multiscreensite.com/fac18167cc14456196ba71cef32d4bc0/siteTemplateIcons/fViD6lOeQZmv89Yvf7vM_Blank_services_BigPreview.jpg",
    "desktop_thumbnail_url": "https://irp-cdn.multiscreensite.com/fac18167cc14456196ba71cef32d4bc0/siteTemplateIcons/JcFd47BRSmOv8utqovg3_blank_services_desktop.png",
    "tablet_thumbnail_url": "https://irp-cdn.multiscreensite.com/fac18167cc14456196ba71cef32d4bc0/siteTemplateIcons/Mva1521TEK3O936gia2F_blank_services_tablet.png",
    "mobile_thumbnail_url": "https://irp-cdn.multiscreensite.com/fac18167cc14456196ba71cef32d4bc0/siteTemplateIcons/xNEqNg6ZR56eI3ngAxvE_blank_services_mobile.png",
    "template_id": 1003738,
    "template_properties": {
      "can_build_from_url": false,
      "has_store": false,
      "has_blog": false,
      "page_count": 3,
      "type": "duda"
    }
  },
  {
    "template_name": "Conference",
    "preview_url": "http://dashboard.russjeffery.com/preview/dm-theme-1004580-en-320",
    "thumbnail_url": "https://irp-cdn.multiscreensite.com/c3e028f9d55f47dfbde4c4c237ffda9f/siteTemplateIcons/LgJaTshSpaGY709UMa5f_BigPreview%20(2).jpg",
    "desktop_thumbnail_url": "https://irp-cdn.multiscreensite.com/c3e028f9d55f47dfbde4c4c237ffda9f/siteTemplateIcons/10xwaGtIQX6GQziGsTXs_conference_desktop.png",
    "tablet_thumbnail_url": "https://irp-cdn.multiscreensite.com/c3e028f9d55f47dfbde4c4c237ffda9f/siteTemplateIcons/RezGoJXWQWWbOkd73RBI_conference_tablet.png",
    "mobile_thumbnail_url": "https://irp-cdn.multiscreensite.com/c3e028f9d55f47dfbde4c4c237ffda9f/siteTemplateIcons/r4gs9oeLQz8JItdoilAL_conference_mobile.png",
    "template_id": 1004580,
    "template_properties": {
      "can_build_from_url": false,
      "has_store": false,
      "has_blog": false,
      "page_count": 3,
      "type": "duda"
    }
  }
]
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api.duda.co/api/sites/multiscreen/templates \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Get Template

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="get" summary="Get Template" path="/sites/multiscreen/templates/{template_id}" %}
{% swagger-description %}
Get the details of a Template.

The 'template\_properties' object also has two more fields than are listed. there are: 'type' and 'visibility' fields. Both of these are strings.
{% endswagger-description %}

{% swagger-parameter in="path" name="template_id" type="string" required="true" %}
ID associated with a template.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="lang" type="string" %}
Retrieve templates for specific languages.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "template_name": "Consultant Landing Page",
  "preview_url": "http://dashboard.russjeffery.com/preview/dm-theme-1026287-en-343",
  "thumbnail_url": "https://irp-cdn.multiscreensite.com/c1e7738d32ae46538527c1fd4e95a9b9/siteTemplateIcons/4CXbg61CTvKDPTEyC7EQ_Consultant_landing_page_3%20screens.png",
  "desktop_thumbnail_url": "https://irp-cdn.multiscreensite.com/c1e7738d32ae46538527c1fd4e95a9b9/siteTemplateIcons/jASytIEDRJWRG0dxSbJj_Consultant_landing_page_Desktop.png",
  "tablet_thumbnail_url": "https://irp-cdn.multiscreensite.com/c1e7738d32ae46538527c1fd4e95a9b9/siteTemplateIcons/4XZxi7HCTWaPx7oTc6fW_Consultant_landing_page_Tablet.png",
  "mobile_thumbnail_url": "https://irp-cdn.multiscreensite.com/c1e7738d32ae46538527c1fd4e95a9b9/siteTemplateIcons/8V63M24zRYaJG96sWSdu_Consultant_landing_page_Mobile.png",
  "template_id": 1026287,
  "template_properties": {
    "can_build_from_url": false,
    "has_store": false,
    "has_blog": false,
    "page_count": 1,
    "type": "duda"
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api.duda.co/api/sites/multiscreen/templates/template_id \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Update Template

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Update Template" path="/sites/multiscreen/templates/{template_id}" %}
{% swagger-description %}
Update the name of a custom Template.
{% endswagger-description %}

{% swagger-parameter in="path" name="template_id" type="string" required="true" %}
ID of an existing 

**custom**

 template.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="new_name" type="string" %}
The new name to assign to the template.
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="warning" %}
**Heads up: Only available for custom/team templates**

Attempting to update a Duda template will return an 'Access is Forbidden' error.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/sites/multiscreen/templates/template_id \
     --header 'accept: application/json' \
     --header 'content-type: application/json'
```
{% endtab %}
{% endtabs %}

## Create From Site

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Create From Site" path="/sites/multiscreen/templates/fromsite" %}
{% swagger-description %}
Create a new Template based on an existing Site.
{% endswagger-description %}

{% swagger-parameter in="body" name="site_name" type="string" %}
The unique identifier of the source site
{% endswagger-parameter %}

{% swagger-parameter in="body" name="new_template_name" type="string" %}
The name to associate with the new template.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "template_name": "Example Template",
  "preview_url": "http://example.mobilewebsiteserver.c...eview/365dd849",
  "thumbnail_url": "https://dp-cdn.multiscreensite.com/t...nd=[B@311b938d",
  "template_id": 1000408,
  "template_properties": {
    "can_build_from_url": false
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/sites/multiscreen/templates/fromsite \
     --header 'accept: application/json' \
     --header 'content-type: application/json'
```
{% endtab %}
{% endtabs %}

## Create From Template

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="post" summary="Create From Template" path="/sites/multiscreen/templates/fromtemplate" %}
{% swagger-description %}
Create a new Template based on an existing one.
{% endswagger-description %}

{% swagger-parameter in="body" name="template_id" type="int32" %}
ID of the source template.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="new_template_name" type="string" %}
The name for the new template.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="object" %}
```json
{
  "template_name": "Example Template",
  "preview_url": "http://example.mobilewebsiteserver.c...eview/365dd849",
  "thumbnail_url": "https://dp-cdn.multiscreensite.com/t...nd=[B@311b938d",
  "template_id": 1000408,
  "template_properties": {
    "can_build_from_url": false
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know: The thumbnail\_url is not generated immediately**

Duda will automatically generate a thumbnail image of the template as an asynchronous process that is often available a while after the initial template creation.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/sites/multiscreen/templates/fromtemplate \
     --header 'accept: application/json' \
     --header 'content-type: application/json'
```
{% endtab %}
{% endtabs %}

## Delete Template

{% swagger baseUrl="https://api.duda.co/api" expanded="false" method="delete" summary="Delete Template" path="/sites/multiscreen/templates/{template_id}" %}
{% swagger-description %}
Delete a custom Template.
{% endswagger-description %}

{% swagger-parameter in="path" name="template_id" type="string" required="true" %}
ID of the template to delete.
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
**Good to Know: Only available for custom/team templates**

Attempting to delete a Duda template will return an 'Access is Forbidden' error.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request DELETE \
     --url https://api.duda.co/api/sites/multiscreen/templates/template_id \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
