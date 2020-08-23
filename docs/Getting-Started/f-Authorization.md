# Authorization

Rippling integrations rely on OAuth 2.0, in which RIppling is the server and your application is the client.

At a high-level Rippling will send a user with a ?code=<xxx> parameter when they install your application on Rippling. This is the authorization that you rapplication will utilize to exchnage for access and refresh tokens.



### The Installation Flow

To begin, go to ​https://stage.rippling.com/login to login with your Rippling-provided staging account credentials.

Once logged in, you will proceed directly to the URL of your application. ​https://stage.rippling.com/apps/PLATFORM/<appName>​.

As you go through the setup flow, you will be redirected to the Redirect URL that you provided in your Development Package. The following query parameters will be present in the redirect.

