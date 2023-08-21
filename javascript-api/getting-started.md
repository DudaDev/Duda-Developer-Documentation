# Getting Started

Duda's **Javascript API** allows you to get access to common helper functions or specific actions taken on a website. The JS API can be used in conjunction with javascript code for Widget Builder or with individual Duda Responsive Websites.

### Overview

This JS API is available with every website and loads asynchronously. The object is always available under the global `dmAPI` namespace.

It is strongly recommended to place any code using Duda's JS api in the body-end.html file. If placed elsewhere on the page (ex. header or body), you risk the website not being [page speed optimized](https://help.duda.co/hc/en-us/articles/115002313908-Google-PageSpeed).

### How to use the API

The best and easiest way to add this code to individual websites is to place it in the body-end, found in [developer mode](https://help.duda.co/hc/en-us/articles/229312887-Developer-Mode).

If done correctly, it should look like this in Developer Mode.

<figure><img src="https://files.readme.io/4e31a6b-js-api-dev-mode.jpg" alt=""><figcaption></figcaption></figure>
