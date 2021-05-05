---
tags: [authorization, installation, match, token, quick-start]
---

# Authorization

Rippling integrations rely on OAuth 2.0, in which Rippling is the server and your application is the client. At a high-level Rippling will send the user to your redirect URL with a `?code=<xxx>` parameter when they install your application on Rippling. This provides the authorization that your application will utilize to exchange for access and refresh tokens.

## The Installation Flow

The following flow walks you through the installation of an application on Rippling's Sandbox Environment. The process is the same on the Rippling Production Environment, but you will replace `sandbox.rippling.com/api/platform/api` with `api.rippling.com/platform/api` in your API calls. To login on production, you will access `app.rippling.com`.

To begin, go to `​https://sandbox.rippling.com/login` to login with your Rippling-provided sandbox account credentials. Once logged in, you should proceed directly to the URL of your application. `​https://sandbox.rippling.com/apps/PLATFORM/<appName>`​, as it will not yet be discoverable.

### Initial Redirect

As you go through the setup flow, you will be redirected to the Redirect URL that you provided in your [development package](https://developer.rippling.com/docs/rippling-api/docs/Getting-Started/c-Partners.md#submit-your-development-package). The following query parameters will be present in the redirect.

| Redirect Query Parameter | Description                                                                                                               |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| code                     | OAuth code that can be exchanged for an access token.                                                                     |
| buy                      | A boolean value based on whether the user indicated they are purchasing a new account, or connecting an existing account. |
| redirect_uri             | The URL on Rippling that the user should be sent back to once the OAuth setup is done.                                    |

Using the code value, your server will be able to get an access token from Rippling.

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
curl -X POST -H "Authorization: Basic REDACTED" -F "grant_type=authorization_code" -F "code=qcpSVhN584QxCm6tEITWk4Bxaz5Zci" -F "redirect_uri=http://mysite.com/my_redirect_uri" "https://sandbox.rippling.com/api/o/token/"
```

Here is an access token sample response:

```json
{
  "access_token": "REDACTED", 
  "token_type": "Bearer",
  "expires_in": 129600, 
  "refresh_token": "REDACTED",
  "scope": "employee:workEmail employee:name"
}
```

### Refresh Tokens

To retrieve a Refresh Token, send a POST request to the same URL `https://sandbox.rippling.com/api/o/token/` with basic auth and the following form parameters.

| Refresh Query Parameters | Description                          |
| ------------------------ | ------------------------------------ |
| grant_type               | refresh_token                        |
| refresh_token            | Refresh token from the initial grant |

## Matching

Now that the connection has been made, your server should request the Company and Employee Information. This information can then be matched with your application's internal database.

### Current Company

Retrieve the current company's information with the GET companies/current endpoint. Note, the fields returned will depend on the scopes the customer has authorized your service to access.

<!--
type: tab
title: Request
-->

```js
curl --location --request GET 'https://api.rippling.com/platform/api/companies/current' \
--header 'Authorization: Bearer REDACTED'
```

<!--
type: tab
title: Response
-->

```json
{
    "id": "595f75ffd2a5f80ae22ce88e",
    "ein": "123121111",
    "address": {
        "city": "San Francisco",
        "state": "CA",
        "country": "US",
        "zip": "94110",
        "streetLine1": "3000 Mission Street"
    },
    "tax_info": {
        "ein": "123121111",
        "entityType": "C_CORP",
        "incorporationDate": null,
        "soleProprieterSSN": null,
        "futaExempt": false,
        "signatory": {
            "id": "5d3777868a9f4e2b5e467fc9",
            "name": "Support Account",
            "firstName": "Support",
            "lastName": "Account",
            "dob": "2020-03-01",
            "ssn": "",
            "phone": null,
            "title": "VP of engineering",
            "workEmail": "supportnew@testrippling.com",
            "signableName": "Support Account"
        },
        "nameWithIrs": null,
        "incorporationState": null,
        "entityName": "Aamir Prod [Test]",
        "dba": null,
        "postalAddress": null
    },
    "workLocations": [
        {
            "id": "5984bca87ee766438fd6faa5",
            "nickname": "SF",
            "address": {
                "city": "Salem",
                "zip": "97317",
                "streetLine1": "4000 Mission Street Southeast",
                "country": "US",
                "state": "OR",
                "steLocationCode": {
                    "cityCode": "0004491020",
                    "psdCode": "",
                    "schoolCode": "",
                    "countyCode": "047",
                    "stateCode": "41",
                    "municipalityCode": "",
                    "transitDistrictCode": "",
                    "locationCode": "41-047-0004491020"
                }
            }
        }   
    ],
    "subscription": null,
    "primaryEmail": "aamir+prod@rippling.com",
    "phone": "9892471335",
    "name": "Bob's Bakery"
}
```

<!-- type: tab-end -->

### Employees

Retrieve the current company's employees information with the GET /employees endpoint. If an employee already has an account within your application, you should enable the admin to match the existing account or create a new account.

For any users that need to create a new account, you should be able to retrieve most of the data that is needed from Rippling's API. Your application will then be able to rely on the employees returned from this endpoint to create and suspend accounts.

Note, the fields returned will depend on the scopes the customer has authorized your service to access.

<!--
type: tab
title: Request
-->

```js
curl --location --request GET 'https://api.rippling.com/platform/api/employees' \
--header 'Authorization: Bearer REDACTED'
```

<!--
type: tab
title: Response
-->

```json
[
    {
        "id": "5c8f7f06c592917aeee1ea9f",
        "name": "John Doe",
        "preferredFirstName": "John",
        "firstName": "John",
        "employmentType": "SALARIED_FT",
        "lastName": "Doe",
        "phoneNumber": "819-729-4862",
        "dob": "2020-03-01",
        "phone": "819-729-4862",
        "title": "Director of Product",
        "department": "Engineering",
        "workLocation": {
            "city": "Salem",
            "zip": "97317",
            "streetLine1": "4000 Mission Street Southeast",
            "country": "US",
            "state": "OR",
            "steLocationCode": {
                "cityCode": "0004491020",
                "psdCode": "",
                "schoolCode": "",
                "countyCode": "047",
                "stateCode": "41",
                "municipalityCode": "",
                "transitDistrictCode": "",
                "locationCode": "41-047-0004491020"
            }
        },
        "address": null,
        "flsaStatus": "non-exempt",
        "personalEmail": "x@testrippling.com",
        "spokeId": null,
        "ein": "123121111",
        "endDate": null,
        "updatedAt": "2020-08-11T21:59:23+0000",
        "createdAt": "2019-03-18T11:20:38+0000",
        "startDate": "2019-03-29",
        "employeeNumber": 11,
        "roleState": "ACTIVE",
        "workEmail": "parashuram@aamirkhan.co.in",
        "offerAcceptedDate": "2019-03-18",
        "manager": "5d3777868a9f4e2b5e467fc9"
    }
]
```

<!-- type: tab-end -->
