# Check App Store Health

{% swagger method="post" baseUrl=" https://api-sandbox.duda.co/api" expanded="true" fullWidth="false" path="/integrationhub/application/health" summary="" %}
{% swagger-description %}
Check if the Duda App Store service is running!

Most Apps don't need this at all. It might be helpful to detect full outages.
{% endswagger-description %}

{% swagger-parameter in="header" name="authorization" type="string" required="true" %}
Your App Account's username and password, based64'd.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="curl" %}
```sh
curl --request GET \
     --url https://api-sandbox.duda.co/api/integrationhub/application/health \
     --header 'accept: application/json' \
     --header 'authorization: Basic ZXhhbXBsZVVzZXI6bmljZXRyeQ==' \
     --header 'x-access-token: {access_token}'
```
{% endtab %}
{% endtabs %}
