# Postman

Postman is a tool for streamlining API collaboration and development.

In order to provide an quick path to development, Rippling provides an officially supported Postman collection that can be [accessed here](https://documenter.getpostman.com/view/11475460/T1LQhS1V?version=latest).

Please note, the Rippling Postman collection is intended to provide a launching pad for utilizing the Rippling APIs, but for the most up to date documentation, you should review the [Rippling API documentation](https://rippling.stoplight.io/docs/rippling-api/RipplingOpenAPI.v1.yaml).

For more information on Postman, you can visit [their site](https://www.postman.com/).

In order to generate a Rippling access token using Postman, you will need to provide the following information.

- Token Name: A name for the token of your choosing.
- Grant Type: Authorization Code
- Authorize Using Browser: True
- Auth URL: The Auth URL of your application. This should be of the form: https://app.rippling.com/apps/PLATFORM/{appName}
- Client ID: The client ID you were provided by Rippling.
- Client Secret: The client secret you were provided by Rippling.

Please note, you likely will want to generate access tokens for both the Staging environment as well as the Production environment.

<br />

<div style="position: relative; padding-bottom: 56.25%; height: 0;"><iframe src="https://www.loom.com/embed/6af93506e2c34ca983ca60d65f196f8b" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe></div>