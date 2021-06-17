# OpenID Connect Guide

OIDC-based SSO is one of two SSO options supported by Rippling.
The OpenID Connect (OIDC) is an identity layer built on top of OAuth 2.0 framework. The two major difference in the two flow being that for OIDC:
1. During the initial request, a specific scope of OIDC is used
2. When partner app exchange the auth_code for the access token, the partner app will receive an ID token in addition to the access token.


Please note that to enable OpenID Connect, make sure to reference the [Scopes](https://developer.rippling.com/docs/rippling-api/docs/Getting-Started/e-Scopes.md) section and select `OIDC_SSO` as a required scope when submitting your
[development package](https://developer.rippling.com/docs/rippling-api/docs/Submit/development-package.md).

### Authorization Flow

To send an authentication request, your server will need to make a /GET reqest containing the desired parameters sent to the Authorization Server. In sandbox, this URL is https://sandbox.rippling.com/oidc/v1/authorize. In production, this URL is https://app.rippling.com/oidc/v1/authorize.

| Auth Query Parameters | Description                                                                  |
| --------------------- | ---------------------------------------------------------------------------- |
| Response_type            | input the value `code`                                                           |
| scope                  | Required scopes: `openid` `profile` `email` `address` `phone` separated by space                                    |
| redirect_uri          | The URL on Rippling that the user should be sent back to once the OAuth setup is done. This must match what was provided in the partner package.  |
| state                  | A state string that can be used to remember the state of interaction with the end user.                                     |
| client_id                  | The client_id we provide you with                                     |

**Sample Authentication Request:**
```js
curl --location --request GET 'https://app.rippling.com/oidc/v1/authorize?response_type=code&scope=openid%20profile%20email%20address%20phone&client_id=your_client_ID&state=enter_state_status&redirect_uri=enter_redirect_uri' \
```

### Retrieving the authorization code
Rippling will then authenticate and ask for consent of the end-user. Once consent from the end-user is received, Rippling will direct the end-user back to the client along with an authorization code.

```js
https://client.example.com/v1/callback?code=7IudMqOgZBwgqU6ZimPVIRNpWj3uw4&state=enter_state_status
```

### Retrieving an Access Token

To retrieve the access token, your server will need to make a POST to the Auth URL. In sandbox this URL is `https://sandbox.rippling.com/api/o/token/​`. The POST should include a basic auth header with base64 encoded `<clientid>:<clientsecret>`, along with the following parameters.

| Auth Query Parameters | Description                                                                  |
| --------------------- | ---------------------------------------------------------------------------- |
| grant_type            | authorization_code                                                           |
| code                  | OAuth code that was sent in the redirect                                     |
| redirect_uri          | Your redirect URL. This must match the redirect URL you had provided to Rippling |

> When the user is redirected from Rippling to your app, that user should then sign in to the app. This allows you to identify the account and associate the code with their account. The redirect URL that you receive from Rippling is where you should redirect the user back to following the user signing into the application.
> <br>If the installation process begins from your application, you do not need to redirect the user back to Rippling, following the user getting sent to the app from Rippling. However, if the installation begins from Rippling, we ask the user is redirected back to Rippling.



Here is an access token sample request:

```js
curl -X POST -H "Authorization: Basic REDACTED" -F "grant_type=authorization_code" -F "code=REDACTED" -F "redirect_uri=http://mysite.com/my_redirect_uri" "https://sandbox.rippling.com/api/o/token/"
```

Here is an access token sample response:

```json
{
  "access_token": "REDACTED",
  "token_type": "Bearer",
  "id_token": "REDACTED",
  "expires_in": 129600,
  "refresh_token": "REDACTED",
  "scope": "employee:workEmail employee:name openid"
}
```

### Claims
There are two ways in which you can return claims about the currently authenticated end user. You can do so through decoding the JWT or through using the `/userinfo` endpoint.

#### ID Token

The ID token is a JSON web token (JWT) where partners can decode from base64 format in order to extract data of the user. Once decoded, the `aud` field should match with the client ID we provide you with, the `sub` field corresponds to the role id of the role who is trying to log in.

#### /Userinfo

Alternatively, you can make a GET to /userinfo endpoint. The Access Token obtained from the OAuth request must be sent as a Bearer Token.

Sample request:

```js
curl --location --request GET 'https://api.rippling.com/platform/api/userinfo' \
--header 'Authorization: Bearer REDACTED' \
```

Sample response:

```js
{
    "sub": "5fb2f623a2b0ae0029fb60ea",
    "picture": "https://s3.us-west-2.amazonaws.com/com.rippling.images/d3e8dded-0d07-48bd-838a-65639684091e",
    "name": "James Smiths",
    "family_name": "Smiths",
    "given_name": "James",
    "preferred_username": "James",
    "birthdate": "2017-06-08",
    "gender": "male",
    "email": "sample@email.com",
    "email_verified": true,
    "address": "{\"street_address\": \"1930 Guerrero Street\", \"locality\": \"San Francisco\", \"region\": \"CA\", \"postal_code\": \"94110\", \"country\": \"US\"}",
    "phone_number": "1231232133",
    "phone_number_verified": true
}
```


### Refresh Tokens

To retrieve a Refresh Token, send a POST request to the same URL `https://sandbox.rippling.com/api/o/token/` with basic auth and the following form parameters.

| Refresh Query Parameters | Description                          |
| ------------------------ | ------------------------------------ |
| grant_type               | refresh_token                        |
| refresh_token            | Refresh token from the initial grant |
