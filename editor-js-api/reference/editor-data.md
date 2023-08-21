# Editor Data

### &#x20;Account

`platform.data.account`

Information about the account logged into the platform. This can be accessed within the editor and dashboard.

<table><thead><tr><th width="281.5">Property</th><th>Description</th></tr></thead><tbody><tr><td><strong>name</strong></td><td>The account that is using the editor/dashboard.</td></tr><tr><td><strong>type</strong></td><td>The type of account that is using the editor/dashboard. Will have a value of either STAFF or CLIENT.</td></tr><tr><td><strong>permissionGroup.name</strong></td><td>An object containing the name of the permission group a STAFF member is assigned to.<br><strong>Note:</strong> Custom groups will return the ID of a permission group. Use the <a href="../../reference/partner-api-reference/team-permissions.md#list-custom-team-group">List Custom Team Groups</a> API to collect the name of the group.</td></tr></tbody></table>

### Site

`platform.data.site`

The site that is being edited. This can only be accessed within the editor.

<table><thead><tr><th width="263.5">Property</th><th>Description</th></tr></thead><tbody><tr><td><strong>name</strong></td><td>The site that is being edited.</td></tr><tr><td><strong>externalUID</strong></td><td>The externalUID of the site (if assigned).</td></tr></tbody></table>
