# App Categories

The Apps are displayed in categories to make it easier for users to find Apps. This improves discoverability and the overall user experience.

### Assigning an App to a category:

In your App Manifest, you can configure to which categories your application will be assigned to:

{% tabs %}
{% tab title="JSON" %}
```json
{
  ...other manifest settigns,
  "category": ["string","string"]  
}
```
{% endtab %}
{% endtabs %}

* An app can be assigned to multiple categories.
* Categories passed to the manifest can be case-insensitive

### Categories Reference

Below is a list of currently available categories.

| Category display name     | Category manifest value   |
| ------------------------- | ------------------------- |
| Accessibility             | Accessibility             |
| Analytics & data          | Analytics\_Data           |
| Booking & events          | Booking\_Events           |
| Communication             | Communication             |
| Content, marketing & CRM  | Content\_Marketing\_CRM   |
| Data privacy & compliance | Data\_Privacy\_Compliance |
| SEO                       | SEO                       |
| Selling online            | Selling\_online           |
| Site enhancements         | Site\_Enhancements        |
