# Deep Links

Duda supports deep links to the App Store from outside the platform.

### Potential use cases

1. Send users to the app's iframe from transactional communications (email, SMS, etc.)
2. Send users to upgrade the app
3. Sending users to install the app on a site

### Setting the domain

Please note that since Duda allows the agencies to white-label the editor, the domain is different for each agency.\
You can get the domain for each site using GET Branding API, under dashboard\_domain

### Links formats

* Open the iframe: https://{dashboard\_domain}/home/site/{siten\_name}?appstore\&appId={app\_uuid}
* Open the installation flow: https://{dashboard\_domain}/home/site/{siten\_name}?appstore\&appId={app\_uuid}\&add=true
* Open the upgrade flow: https://{dashboard\_domain}/home/site/{siten\_name}?appstore\&appId={app\_uuid}\&upgrade=true
* Open the upgrade flow with a specific plan: https://{dashboard\_domain}/home/site/{siten\_name}?appstore\&appId={app\_uuid}\&upgrade=true\&planId={plan\_uuid}
