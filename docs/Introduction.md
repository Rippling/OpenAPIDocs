---
tags: [Intro]
---

# Rippling's API Platform

Rippling requires that all application partners build integrations within [Rippling's App Shop](rippling.com/app-shop). The Rippling App Shop provides a means of showcasing your application to Rippling's clients, as well as securely acquire the proper permissions to access the data needed for your integration. If you are interested in building an application with Rippling, please reach out to apps.partnerships@rippling.com

The API will continue to evolve as more endpoints and capabilities are added. If there are specific endpoints or features that you need developed for your use case, please email apps@rippling.com.

Please note, it is in violation of Rippling's Terms of Service to use a an API key in order to access the Rippling development platform, if that API key does not belong to your organization.

## Partner Applications

To get started with building an application on Rippling, we will need several configuration properties for your application.

URL           | Description
--------------|---------------------------------------------------------------------------------------------------------------------------------------
Redirect URLs | You have the option to provide two redirect URLs: Staging Redirect URL and Production Redirect URL.
SSO URLs      | You have the option to provide two SSO URLs: Staging SSO URL and Production SSO URL. These rely on Rippling's authentication tokens to allow users to sign-in.
Webhook URL  |  You have the option to provide one Webhook URL: Production Webhook URL. *Rippling does not support Webhooks on our staging environment.*

Additionally, you will need to provide Rippling with your application scopes. These scopes are transparently displayed to Rippling customer's that choose to install the application.

Scopes           | Description
-----------------|---------------------------------------------------------------------------------------------------------------------------
company          | The parent company scope. This is a prequisite to additional company:* scopes, but does not serve as a scope superset.
employee         | The parent employee scope. This is a prerequisite to additional employee:* scopes, but does not serve as a scope superset.
company:activity | Permission to read information regarding the company's activity.
company:address  | Permission to read the company's address.
company:phone    | Permission to read the company's phone information.



## Customer Integrations




**This initial guide will discuss how to build an application on Rippling with flavorful markdown!**

```
Neat Stuff
```

> This is a block quote... also looks good.
>> And this is a nested block quote


* Lists
* Are
* Easy too



