---
tags: [development package, Intro, partners]
---

# Partner Requirements


To develop an integrated application on Rippling, you will follow the development process listed below. Please note Rippling partners must use OAuth as outlined in our [Authorization guide](https://developer.rippling.com/docs/rippling-api/docs/Getting-Started/f-Authorization.md).


<!-- theme: success -->

> 1. [Submit your Development Package](https://developer.rippling.com/docs/rippling-api/docs/Getting-Started/c-Partners.md#1-submit-your-development-package)
> 2. [Build the Integration Against Rippling's Sandbox Environment](https://developer.rippling.com/docs/rippling-api/docs/Getting-Started/c-Partners.md#2-build-the-integration-against-ripplings-sandbox-environment)
> 3. [Build the Integration Against Rippling's Production Environment](https://developer.rippling.com/docs/rippling-api/docs/Getting-Started/c-Partners.md#3-build-the-integration-against-ripplings-production-environment)
> 4. [Launch Integration](https://developer.rippling.com/docs/rippling-api/docs/Getting-Started/c-Partners.md#4-launch-the-integration)

This process ensures that all Rippling integrated applications are lauched properly and provide the best possible user experience to our shared customers.

<!-- theme: success -->

> 💡 Check out the [Rippling App Shop](https://rippling.com/app-shop), where all of Rippling's partner applications are listed!


### 1. Submit your Development Package

To get started with building an integration on Rippling you will need to submit a [Rippling Development Package](https://developer.rippling.com/docs/rippling-api/docs/Submit/development-package.md).

Refer to [this page](https://developer.rippling.com/docs/rippling-api/docs/Submit/development-package.md) for more information on what is included in the development package. We generally try to respond to all requests within two weeks, but the exact timing may vary depending on the total number of inbound requests received.


### 2. Build the Integration against Rippling's Sandbox environment

Once your [development package](https://developer.rippling.com/docs/rippling-api/docs/Submit/development-package.md) has been reviewed and approved, you will receive your Rippling App Testing Package to test and build the integration in Sandbox. The Rippling App Testing Package consists of the following information:

- Sandbox Client ID
- Sandbox Client Secret
- Application Name
- Sandbox Account Credentials for testing

There are two ways that customers can install a partner app once launched:

- **Required installation flow:**
Customers can start from your dedicated App shop landing page which we will provide to you (https://app.rippling.com/app-shop/app/{APPNAME}). This flow is required for all partner apps and we've provided a video to demonstrate the end user experience of installing a partner application from the Rippling App Shop. Please note, customer subdomains are not a requirement. We also recommend that partners implement the return flow (https://app.rippling.com/apps/PLATFORM/{APPNAME}/redirect) after users have been redirected to the third party application and is authenticated. This provides a more consistent user flow.
<br />

<div style="position: relative; padding-bottom: 56.25%; height: 0;"><iframe src="https://www.loom.com/embed/734f18e6225c46229cb74d4cacfcad45" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe></div>

- **Optional installation flow:** Customers can also start the integration process from the partner app. This flow is optional and does not have to be implemented.


Once the integration has been built against Rippling’s sandbox environment, use this [Airtable Submission Form](https://airtable.com/shrQa3q3bkeuK6lTQ) to upload videos that demonstrate the end-to-end implementation of all installation flows in Sandbox.

Make sure to select ‘Sandbox’ in the Airtable form when submitting the demo videos for the Sandbox integration. On a high level, you will have to include details regarding the following items when submitting the form for Sandbox:
- **Demo videos:** Please upload videos that demonstrate the end-to-end implementation of all installation flows in Sandbox.
- **Details regarding integration:** We require you to answer a series of questions that will help provide more context on the integration. This may be shared with potential customers, so please ensure to answer the questions as accurately as possible.


### 3. Build the Integration against Rippling's Production environment

Once the Sandbox integration has been approved by the Rippling, we will send you a new App Testing Package that consists of all the information required to test and build against our Production environment.

When you have completed the implementation for Production, use this same [Airtable Submission Form](https://airtable.com/shrQa3q3bkeuK6lTQ) and this time, select ‘Production’.

Below outlines a summary of all required items when submitting the production form:
- **Demo videos:** Please upload videos that demonstrate the end-to-end implementation of all installation flows in Production.
- **Referral Battlecard:** The partner must fill out the [Rippling Partner Battlecard](https://airtable.com/shr4YXl8kPCS1PDgg) ahead of the production release of the integration. The Battlecard will help our Sales team push leads to your team once the integration is live.
- **Production test account:** The partner must provide Rippling with a production test account for the partner app ahead of the production release of the integration.
- **Timing for going live:** partners have the option to go live as soon as the app is approved, or at a later specified date.

Only when Rippling has approved this production video can partners have customers install the integration on production. Partners should not use Rippling's logo or name before receiving approval of the production video.


### 4. Launch the Integration

Once steps 1 - 3 are completed and the production video receives approval from the Rippling team, the application will be made publicly visible and searchable in the Rippling App Shop.


### Frequently Asked Questions

#### Why is there a beta tag attached to my application in the Rippling app shop?

![APIKey](../../assets/images/Beta_Tag.png)

Please note that there will be a beta tag attached to all applications when initially launched. The beta tag will be removed if either of the following conditions is met:
- The app receives 5 or more installs
- The app has been live for a month or longer

#### How do I change my listing assets?
Partners are welcome to update your listing assets at any point. To do so, please email us at developer.support@rippling.com and include the relevant changes that should be made. For more details on best practices for Rippling Application listing, please see [here](https://go.rippling.com/rs/345-FHM-674/images/Rippling_Partner_App_Listing.pdf).

#### Are there any costs or fees associated with building an API integration with Rippling?
The usage of the Rippling API is completely free to partners as of now.
