# Deploying and Releasing Apps

Making apps available in production is called **releasing**. In the release process, Duda takes the exact App manifest as it exists on the sandbox environment and copies it to all Duda production environments. Duda will create the app in our production environment after you first publish the App.

Deploying an App today is done only by Duda. Duda can quickly deploy an App with a few clicks, but, it must manually be done by us. Before publishing, Duda 'locks' the manifest to stabilize the version published to production. During the locking period, trying to update the manifest will return an error.

### Safely deploying

It's important that your App Manifest be pointing to production environments before asking Duda to deploy a change. Since we copy the exact manifest, as is, please ensure that your App is production ready to deploy before Duda deploys it on your behalf.

This means you should double-check if your manifest has endpoints (install, uninstall, etc..) that are not pointing to some test, local, or sandbox environment on your side.

### Non-updateable options

If you change your App **Webhooks** OR **Scopes** in the manifest and the manifest is released, sites that have installed the App before that release will NOT have access to those new scopes or webhooks. If it's important you start getting those, please contact Duda to discuss.
