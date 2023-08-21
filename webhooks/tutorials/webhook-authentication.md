# Webhook Authentication

Duda can sign requests using the HMAC-SHA256 algorithm to allow your app to verify the authenticity of the sender (Duda) and of the payload.

{% hint style="info" %}
**Heads up: This feature is available only for managed accounts**

To get access to this feature, please contact your account manager or Duda support.
{% endhint %}

### Comparing signatures

The signature value is calculated as follows:

1. You should concatenate the timestamp (passed in the `x-duda-signature-timestamp` header) with the body message, separated by a period. `const message = timestamp + "." + bodyString`.
2. The secret key given to you by Duda should be base64 decoded.
3. Generate an HMAC Hash using the `sha256` algorithm from the variables above. Ensure the output is in **binary** (for example, PHP defaults to hex).
4. Base64 encode the resulting HMAC Hash.
5. Compare the encoded HMAC Hash to the signature you received in the `x-duda-signature` header in the request. If they don't match, throw an error and stop all execution.

### An example with data

The request body is `{'key1':'world','key2':'world'}` the timestamp (`x-duda-signature-timestamp` header) is `1570350275357` and our secret key is `mysecretsecret`.

Calculating `base64(hmac-sha256(secret-key, timestamp + "." + message))` results in `+DCfT1wIMUiaZnlZB4u59/d5wkXKA89lv67Ov66vnyc=` which is the value we will find in `x-duda-signature` header of the signed request.

### Code examples

{% tabs %}
{% tab title="Java" %}
```java
String getHMAC(String timestamp,String message) {
        String secretKey = ...;
        SecretKeySpec signingKey = new SecretKeySpec(secretKey.getBytes(StandardCharsets.UTF_8), "HmacSHA256");

        String input = timestamp + "." + message;
        Mac mac = Mac.getInstance("HmacSHA256");
        mac.init(signingKey);
        byte[] rawHmac = mac.doFinal(input.getBytes(StandardCharsets.UTF_8));
        return new String(Base64.getEncoder().encode((rawHmac)));
}


String body = request.getBody();
String timestamp = request.getHeader("x-duda-signature-timestamp");

String hmac = getHMAC(timestamp, body);
String signautreHeader = request.getHeader("x-duda-signature");

assert hmac.equals(signautreHeader);
```
{% endtab %}

{% tab title="Node" %}
```javascript
const crypto = require('crypto');

const sig = req.headers["x-duda-signature"];
const time = req.headers["x-duda-signature-timestamp"];
const body = JSON.stringify(req.body);

const decoded = Buffer.from(<secret-key>, "base64").toString("utf8");
const check = crypto.createHmac("sha256", decoded)
    .update(`${time}.${body}`)
    .digest("base64");

assert(sig === check);
```
{% endtab %}

{% tab title="PHP" %}
```php
<?php
//Make sure that it is a POST request
if(strcasecmp($_SERVER['REQUEST_METHOD'], 'POST') != 0){
    throw new Exception('Request method must be POST!');
}

//Make sure that the content type of the request is application/json
$contentType = isset($_SERVER["CONTENT_TYPE"]) ? trim($_SERVER["CONTENT_TYPE"]) : '';
if(strcasecmp($contentType, 'application/json') != 0){
    throw new Exception('Content type must be: application/json');
}

//Receive the RAW post data
$body = trim(file_get_contents("php://input"));

//Recieve custom headers and set variables
$headers = getallheaders();
$sigToVerify = $headers['x-duda-signature'];
$timestamp = $headers['x-duda-signature-timestamp'];

//Concat message to be hashed later.
$message = $timestamp . '.' . $body;

//Decode Base64 Secret from Duda
$secret = base64_decode('<B64_SECRET_GOES_HERE>');

//Generate hmac with data passed and the secret. Then base64 encode.
$hmac = base64_encode(hash_hmac('sha256',$message,$secret,true));

// Compare recieved base64 sig to sig generated. They should match.
if($sigToVerify == $hmac) {
      echo 'Signature verified, proceed!';
}
```
{% endtab %}
{% endtabs %}
