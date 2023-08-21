---
description: Logging users into your application from within Duda.
---

# Single Sign-On

All Duda Apps have some dashboard or portal that users must log into in order to manage the settings of the App. Single Sign-on (SSO) enables users to seamlessly authenticate from Duda into your App, directly, without needing a username and password to login.

SSO is a core aspect of integrating into Duda, as it ensures that there's a quick and seamless experience when users try and access your App from within the Duda environment.

<figure><img src="https://files.readme.io/4602728-app-sso-example.gif" alt="1470"><figcaption><p>Example of a user SSOing into an App within Duda.</p></figcaption></figure>

The primary experience is for Apps to be embedded within the Duda experience (shown above). This is done by opening the app portal inside of an iframe and having the App authenticate the user.

We have full [App SSO Reference](../reference/sso.md) in the documentation.
