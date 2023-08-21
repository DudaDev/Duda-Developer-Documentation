---
description: SSOing into your App from within Duda.
---

# SSO

When users access your UI via an iframe in Duda's editor, Duda will render an iframe to the URL specified in the manifest under `base_sso_url` with additional query parameters to allow you to authenticate the user into your App.

The URL format is: `{{base_sso_url}}?site_name={{site name}}&timestamp={{time stamp}}&lang={{use langauge code}}&is_white_label={{false}}&editor_origin={{https://editor.example.com}}&sdk_url={{SDK URL}}&current_user_uuid={{user uuid}}&secure_sig={{signature}}&editor_origin={{duda.dashboard.com}}`

There are two types of parameters that Duda attaches here:

SSO Parameters

| Parameter       | Description                                                                                                                          |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **timestamp**   | The timestamp on Dudas servers that was used to generate the SSO Signature.                                                          |
| **site\_name**  | The unique site\_name that is being logged into. You should already have created access once the App was installed for this website. |
| **sdk\_url**    | The URL of the JS SDK that can be used to interact with the Duda editor.                                                             |
| **secure\_sig** | The signature that was signed by the private key, stored within Duda. You can **decode** this using the public key.                  |

Informational Query Parameters:

|                         |                                                                                                                                     |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| **lang**                | Language of the active user in the Duda platform.                                                                                   |
| **is\_white\_label**    | A flag indicating if the user is considered white labeled (does not see Duda branding).                                             |
| **current\_user\_uuid** | The current user's UUID within the Duda platform.                                                                                   |
| **editor\_origin**      | The origin (protocol + host) of the parent URL where the user was logged into. Since Duda is white-labeled, this can be any domain. |

Duda passes a signature signed by the app-specific private key (which Duda stores). You should verify the SSO signature to validate that the user should be allowed to log in. Use the public key in your app's **manifest to verify the signature by decrypting it**.

Duda formats our keys using PKCS#1 (default for RSA) with a 2048 bit key length. Duda URL encodes the entire URL string before redirecting the user to that URL, so you should be sure to URL decode each value passed. This is the same as: [RFC3986](https://tools.ietf.org/html/rfc3986#section-3.4).

You should verify the data by concatenating the `site_name`, `sdk_url`, and `timestamp` with a colon between each. See the following examples:

{% tabs %}
{% tab title="JavaScript" %}
```javascript
async authenticateAPI(payload: AuthDudaInterface): Promise<boolean> {
  if (
    !payload?.sdkUrl ||
    !payload?.timestamp ||
    !payload?.secureSig ||
    !payload?.siteName
  ) {
    throw new Error('Bad User Input: all fields are mandatory');
  }
  const { sdkUrl, secureSig, siteName, timestamp } = payload;
  const decodedSignature = decodeURIComponent(secureSig);
  const decodedSdkUrl = decodeURIComponent(sdkUrl);
  const decodedSiteName = decodeURIComponent(siteName);
  const sigDataToVerify = `${decodedSiteName}:${decodedSdkUrl}:${timestamp}`;
  return (
    sigDataToVerify ===
    crypto
      .publicDecrypt(
        '-----BEGIN PUBLIC KEY-----\n' +
          process.env.DUDA_PUBLIC_KEY +
          '\n-----END PUBLIC KEY-----',
        Buffer.from(decodedSignature, 'base64'),
      )
      .toString()
  );
}
```
{% endtab %}
{% endtabs %}

Additionally, Duda encodes the Signature in Base64 before sending it, so you should decode it as well. Most RSA/Crypto libraries have support for base64 decoding as part of the process.

### Time Validity of SSO Links

Apps are expected to refuse SSO links with a timestamp older than 120 seconds before the SSO link HTTP request is received by the App.

Duda cannot technically enforce such a policy. However, Duda will, from time to time, test if Apps are in compliance with this policy.

### User Language

Duda passes the language of the active user in the `lang` query parameter of the SSO link. App's iframe should localize according to this parameter. Note that for each Duda site there can be several users working on different languages, so this should be done at time of SSO.

[The full list of languages in the Duda editor can be found here.](../../reference/app-store-api-reference/#good-to-know)

### Cookie Management

Since your App will load in an iframe by default, web browsers treat your SSO URL as a 3rd party context. In order for you to properly be able to set cookies, you need to make sure that you configure your cookie to properly work in a 3rd party context by setting the `SameSite` attribute to `None`. This informs browsers that the cookie is not from the same parent side and allows to to be set. We recommend reading the MDN documentation on the [SameSite attribute](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie/SameSite).

In conjunction, you also need to use the `secure` flag on cookies, as well.
