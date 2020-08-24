---
tags: [sso, Single Sign-On, Sign-on, Sign on]
---

# Single Sign-On

Single Sign-On, or SSO, is a property of identity and access management systems that allows users to securely authenitcate to your application with their Rippling credentials. The user can typically sign on directly from the application, from Rippling, or both.

<br />

<div style="position: relative; padding-bottom: 56.25%; height: 0;"><iframe src="https://www.loom.com/embed/e6c449912e1d4f319c36946d239fa8cc" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe></div>

Rippling partners can implement single sign-on through two primary methods: **Rippling's Platform SSO** and **SAML SSO**. Before diving in, the user experience of both sign-in methods are essentially the same, although the installation flow varies slightly.

## Rippling Platform SSO

Rippling Partner Applications have the option of providing an SSO endpoint to Rippling in their Development Package.

If the SSO endpoint is configured for you application, Rippling will have the user's browser POST a form to the SSO URL with the folowing form-encoded fields.

SSO Form Fields | Description
----------------|----------------------------------------------------------
code            | OAuth code that can be exchanged for an access token.
roleId          | String identifier for the employee in Rippling.
companyId       | String identifier for the employee's company in Rippling.
accessLevel     | `ADMIN` or `EMPLOYEE`

Your implementation of the SSO URL should exchange the code for an access token, just like the Redirect URL. This verifies that the SSO request legitimately came from Rippling. Your system can then log the user in to your application. You can hit /me endpoint with the access token to get more information about the currently logged in user, if needed.

<!--
type: tab
title: Request
-->
```js
curl --location --request GET 'https://api.rippling.com/platform/api/me' \
--header 'Authorization: Bearer OMITTED'
```
<!--
type: tab
title: Response
-->
```json
{
    "id": "5ec5595dfa9c4e1728118d11",
    "workEmail": "cpitt+2@rippling.com",
    "company": "5ec5595afa9c4e1728118cb5"
}
```
<!-- type: tab-end -->

## SAML SSO

Security Assertion Markup Language (SAML) is an open standard that allows identity providers (IdPs), such as Rippling, to pass authentication and authorization information to service providers (SPs), such as your application!

To integrate your application with SAML SSO, you will leverage the `GET /saml/idp_metadata` endpoint to automatically pull a company's SAML configuration from Rippling. However, you will need provide the Rippling team with clear documentation for users to retrieve their `ACS URL`, `Entity ID`, and any other necessary configuration information. If you'd like to add SAML SSO to your integrated application, please reach out to apps@rippling.com.

