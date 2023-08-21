# SSL Certificates

## Create Certificate

{% swagger method="post" path="/sites/multiscreen/{site_name}/certificate" baseUrl="https://api.duda.co/api" summary="Create Certificate" expanded="false" fullWidth="false" %}
{% swagger-description %}
This will enable a HTTPS connection between site visitors and the Duda platform. It usually takes 15-30 minutes to successfully generate a SSL certificate for a website. You can get the status of the SSL certificate by calling the GET site API and checking the certificate\_status parameter. Once the certificate is successfully generated, all website visitors will be redirected to the HTTPS connection. This can be disabled by setting force\_https value to false in the site object. You do not need to worry about renewing the certificate, as Duda will do this automatically.


{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="warning" %}
**Heads up:** Before sending this API call, it's important that the domain is successfully pointed to Duda's servers. We only currently offer Domain Verified (DV) certificates. As part of the API call, Duda will verify that the domain is correctly pointing at the platform. If it is not, Duda will return an error.
{% endhint %}

{% tabs %}
{% tab title="curl" %}
<pre class="language-sh"><code class="lang-sh">curl --request POST \
<strong>     --url https://api.duda.co/api/sites/multiscreen/site_name/certificate \
</strong>     --header 'accept: application/json'
</code></pre>
{% endtab %}
{% endtabs %}

## Renew Certificate

{% swagger method="post" path="/sites/multiscreen/{site_name}/certificate/renew" baseUrl="https://api.duda.co/api" summary="Renew Certificate" expanded="false" %}
{% swagger-description %}
Duda handles the automatic renewal of SSL certificates every 2.5 months (Our LetsEncrypt based certificates are valid for 3 months). You only need to renew the SSL certificate if you recently changed DNS settings on the domain and need to cover the base domain as part of the SSL certificate
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% hint style="warning" %}
**Heads up:** Can only be done if there is an already existing SSL certificate
{% endhint %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request POST \
     --url https://api.duda.co/api/sites/multiscreen/site_name/certificate/renew \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}

## Delete Certificate&#x20;

{% swagger method="get" path="/sites/multiscreen/{site_name}/certificate" baseUrl="https://api.duda.co/api" summary="Delete Certificate" expanded="false" %}
{% swagger-description %}
Delete a certificate that has been generated for a website. This will ensure that the website is served over only an HTTP (insecure) connection and will delete the generated certificate.
{% endswagger-description %}

{% swagger-parameter in="path" name="site_name" type="string" required="true" %}
A valid site name of an existing website
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request DELETE \
     --url https://api.duda.co/api/sites/multiscreen/site_name/certificate \
     --header 'accept: application/json'
```
{% endtab %}
{% endtabs %}
