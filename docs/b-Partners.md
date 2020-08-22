---
tags: [partners, Intro]
---

# Partner Applications

## The Development Process

To develop an integrated application on Rippling, you will follow the development process listed below.

<!-- theme: success -->

> 1. [Submit your Development Package](https://rippling.stoplight.io/docs/rippling-api/docs/b-Partners.md#submit-your-development-package)
> 2. [Build the Integration Against Rippling's Test Environment](https://rippling.stoplight.io/docs/rippling-api/docs/b-Partners.md#build-the-integration)
> 3. [Receive Approval from the Rippling Development Team](https://rippling.stoplight.io/docs/rippling-api/docs/b-Partners.md#receive-approval-from-rippling)
> 4. [Launch the Integration in Rippling's Production Environment](https://rippling.stoplight.io/docs/rippling-api/docs/b-Partners.md#launch-the-integration)

This process ensures that all Rippling integrated applications are lauched properly and provide the best possible user experience to our customers.

<!-- theme: success -->

> 💡 Check out the [Rippling App Shop](rippling.com/app-shop), where all Rippling partner applications are listed!

### Submit your Development Package

To get started with building an integration on Rippling you will need to submit a Rippling development package over email to [application.partnerships@rippling.com](mailto:application.partnerships@rippling.com).

The Rippling development package should consist of the assets listed below.

- **Application Listing Assets**
- **Configuration Properties**


#### Application Listing Assets

For an example of a Rippling Application listing, please see [here](https://www.rippling.com/app-shop/app/slack).

| Asset                      | Description                                                                                                                                                                                                                                                                                    |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Application Overview       | _Required_ A brief overview of your company's application. This description has a character limit of 180 characters. Note, this can be changed later on, but will be required to register your application.|
| Product Description        | _Required_ An in-depth description of your company's application and its product features. Note, this can be changed later on, but will be required to register your application.|
| Integration Description    | _Required_ An in-depth description of how your application will integrate with Rippling. Note, this can be changed later on, but will be required to register your application.|
| Logo Package               | _Required_ A monotone logo badge to accompany your application listing. While we understand the needs of a logo vary on a case by case basis, we generally ask that you follow our logo requirements listed below. Note, this can be changed later on, but will be required to register your application.|
| App Category | _Required_ The App Shop category that you would your application listed in. See the [Rippling App Shop](rippling.com/app-shop) for the current categories.|
| G2 Crowd URL               | _Optional_ If your application has a G2 Crowd listing, please provide the URL to your listing. The Rippling App Shop relies on G2 Crowd to pull in review.|

**Logo Requirements**

- An SVG file of your logo, highly preferred to be in a monotone representation of your logo. 
- A HEX color that will be used as the background of your SVG logo.

#### Configuration Properties

| Property           | Description                                                                                                                                |
|---------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| Redirect URLs | *Required* Two redirect URLs: a Staging Redirect URL and a Production Redirect URL.                                                            |
| SSO URLs      | *Optional* Two SSO URLs: a Staging SSO URL and a Production SSO URL. These rely on Rippling's authentication tokens to allow users to sign-in. |
| Webhook URL   | *Optional* One Webhook URL: a Production Webhook URL. _Note, Rippling does not support Webhooks on our staging environment._                 |
|Scopes   |*Required* The permission scopes that your application will require. Customers installing your application will need to authorize the application to access these scopes on their behalf.

As noted, you will need to provide Rippling with your application scopes. These scopes are transparently displayed to Rippling customer's that choose to install the application. Each required scope should be explicitly listed in the following format.

- employee
- employee:workEmail
- employee:title

For more information on Rippling scopes, please see [here](https://rippling.stoplight.io/docs/rippling-api/docs/e-Scopes.md).

### Build the Integration

Once your development package has been reviewed, you will receieve your Rippling App Testing Package to test and build the integration. The Rippling App Testing Package consists of the following information.

- Staging Client ID
- Staging Client Secret
- Application Name
- Staging Account Credentials for testing

Please note, if your integration requires access to Webhooks, you will build the integration against Rippling's Production Environment. If this is required, please mention this in the submission of your Devlopment Package.

### Receive Approval from Rippling

Once you have built and tested the integration, the Rippling team may ask for a demo (either live or as a video) of your integration before approval. Once your integration has been approved, Rippling will provide you with the Rippling App Production Package.

- Production Client ID
- Production Client Secret
- Application Name
- Test Account Credentials for testing the application in production

You will then release a production version of your integration that is ready for launch.

### Launch the Integration

To launch the application, the Rippling team will ask for live or recorded demo of your application in order to approve the listing to go live in the Rippling App Shop. Once the team has approved the integration, the application will be made publicly visible in [the Rippling App Shop](rippling.com/app-shop).