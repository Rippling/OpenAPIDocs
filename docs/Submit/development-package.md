---
tags: [development package]
---

# Partner Development Package



The Rippling [Rippling Development Package](https://developer.rippling.com/docs/rippling-api/docs/Submit/development-package.md) should consist of the items listed below.

- **Application Listing Assets**
- **Configuration Properties**

Please note that you will be able to edit the listing assets or configuration properties submitted in the package if changes come up. To do so, email us at developer.support@rippling.com with the requested changes.


#### Application Listing Assets

For an example of a Rippling Application listing, please see [here](https://www.rippling.com/app-shop/app/slack). For more details on how to best format your listing, please refer to this [guide](https://go.rippling.com/rs/345-FHM-674/images/Rippling_Partner_App_Listing.pdf).

| Asset                   | Description                                                                                                                                                                                                                                                                                               |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Application Overview    | _Required_ A brief overview of your company's application. This description has a character limit of 180 characters. Note, this can be changed later on, but will be required to register your application.                                                                                               |
| Product Description     | _Required_ An in-depth description of your company's application and its product features. Note, this can be changed later on, but will be required to register your application.                                                                                                                         |
| Integration Description | _Required_ An in-depth description of how your application will integrate with Rippling. Note, this can be changed later on, but will be required to register your application.                                                                                                                           |
| Logo Package            | _Required_ A monotone logo badge to accompany your application listing. While we understand the needs of a logo vary on a case by case basis, we generally ask that you follow our logo requirements listed below. Note, this can be changed later on, but will be required to register your application. |
| App Category            | _Required_ The App Shop category that you would like your application listed in. See the [Rippling App Shop](https://rippling.com/app-shop) for the current categories.                                                                                                                                                |
| G2 Crowd URL            | _Optional_ If your application has a G2 Crowd listing, please provide the URL to your listing. The Rippling App Shop relies on G2 Crowd to pull in reviews.                                                                                                                                                |

**Logo Requirements**

- An SVG file of your logo, highly preferred to be in a monotone representation of your logo. 
- A HEX color that will be used for the background of your SVG logo file.

#### Configuration Properties

| Property      | Description                                                                                                                                                                               |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Redirect URLs | _Required_ Two redirect URLs: a Sandbox Redirect URL and a Production Redirect URL.                                                                                                       |
| SSO URLs      | _Optional_ Two SSO URLs: a Sandbox SSO URL and a Production SSO URL. These rely on Rippling's authentication tokens to allow users to sign-in.                                            |
| Webhook URL   | _Optional_ Two Webhook URL: a Sandbox Webhook URL and a Production Webhook URL.                                                                                                     |
| Scopes        | _Required_ The permission scopes that your application will require. Customers installing your application will need to authorize the application to access these scopes on their behalf. |

As noted, you will need to provide Rippling with your application scopes. These scopes are transparently displayed to Rippling customer's that choose to install the application. Each required scope should be explicitly listed in the following format.

- employee
- employee:workEmail
- employee:title

The 'company' and 'employee' scopes serves as a prequisite to any additional company:* or employee:* scopes, but does not serve as a scope superset. For more information on Rippling scopes, please see [here](https://developer.rippling.com/docs/rippling-api/docs/Getting-Started/e-Scopes.md).


>Please note that all required fields should be properly filled in. Failure to do so may result in our team not being able to get back to you with the credentials required.



Use this page to submit your Rippling development package to register for a Rippling developer account. Once your information has been reviewed, our team will contact the email you provided with the Sandbox Account Package.

For more information on getiing started as a partner, or the development package, please see the [partners guide](https://developer.rippling.com/docs/rippling-api/docs/Getting-Started/c-Partners.md).

### Submission Form

<script src="https://static.airtable.com/js/embed/embed_snippet_v1.js"></script><iframe class="airtable-embed airtable-dynamic-height" src="https://airtable.com/embed/shrrHh7KDyVZnm4II?backgroundColor=purpleLight" frameborder="0" onmousewheel="" width="100%" height="1868" style="background: transparent; border: 1px solid #ccc;"></iframe>
