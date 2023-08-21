# Introduction

The Duda API allows you to integrate Duda into your website, workflow, or product. It's one of the main starting points for any integration. The API is REST-based with JSON responses.

### Using Duda's Developer Documentation

Duda’s developer documentation is split into four distinct types of articles: How-to, Concepts, Tutorials, and Reference. You can read about each below:

**Concepts**\
Concept articles give an in-depth exploratory look into a topic or feature, what it does, what problems it can solve, and what the benefits are. The goal is to give you enough background information and context so that you can successfully dive into tutorials or how-to’s and leverage that capability to its fullest extent.

**Tutorials**\
Tutorial articles teach you how to use specific features within Duda by explaining how the feature works, how it’s commonly used, and what you need to know to start building with that feature. The goal is to help you get started and gain confidence so you can begin using features independently.

**How To**\
How-to articles provide step-by-step instructions for how to solve specific problems using the Duda API. Frequently, the instructions might involve combining several different APIs to form a complete workflow or solution you need to solve. The goal of how-to articles is to help you understand the necessary steps to implement a specific feature or workflow.

**Reference**\
Reference articles give you the exact technical details you need to know to implement an API or feature. The articles contain the exact method, path or function that you will call to leverage a specific capability.

### API Credentials

You can find API Credentials for your account from within the Duda dashboard. They can be found under the Business Tools > API Access section.

<figure><img src="https://files.readme.io/91afba4-CleanShot_2023-08-17_at_09.37.232x.png" alt=""><figcaption></figcaption></figure>

After getting to API Access, you can find & save your username and password. If it's your first time using the API, you can reset the password. **Note that resetting the password might break if your API keys are in use somewhere else, so, use this with caution!**

<figure><img src="https://files.readme.io/8ef159a-CleanShot_2023-08-17_at_09.38.112x.png" alt=""><figcaption></figcaption></figure>

### Response Codes

All APIs will respond with one of the following response codes:

| Code                 | Description                                                                                                                               |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| **200** OK           | The request was successful and the response body contains the representation requested                                                    |
| **204** No Response  | The request was successful, but there is no information to send back (usually returned by successful non-GET operations)                  |
| **302** Found        | A common redirect response; you can GET the representation at the URI in the Location response header                                     |
| **400** Bad Request  | The data given in the request failed validation. Inspect the response body for details (see Error data structure for details)             |
| **401** Unauthorized | The supplied credentials, if any, are not sufficient to access the resource                                                               |
| **404** Not Found    | Resource is not available under requested URL                                                                                             |
| **500** Server Error | This usually means there was a problem on Duda's end. Double check to make sure your data sent is correct then reach out to Duda for help |

### Error JSON

The applicative validations and errors are returned with 400 (Bad Request) HTTP response code accompanied with the following error structure:

{% tabs %}
{% tab title="JSON" %}
```json
{
  "error_code":"ResourceNotExist",
  "message":"Template with ID '123456' doesn't exist"
}
```


{% endtab %}
{% endtabs %}

| Property        | Type     | Description                                                         |
| --------------- | -------- | ------------------------------------------------------------------- |
| **error\_code** | s_tring_ | Code of the error, i.e. ResourceNotExist InvalidInput InternalError |
| **message**     | s_tring_ | Detailed error message                                              |
