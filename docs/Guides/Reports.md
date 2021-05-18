# Rippling API Guides: Reports

Rippling's Reports API enables the ability for Rippling App Partners and Rippling admins to pull from Rippling's inbuilt reports which includes 3 main master reports: SOC2, Insurance, and Hardware.


## Setting up the Integration

### Getting Started

#### For App Partners:
Before you begin, you'll need to enable Rippling's token authorization. Please the [authorization documentation](https://developer.rippling.com/docs/rippling-api/docs/Getting-Started/f-Authorization.md) for more details on how you will use access tokens to retrieve authorized client information. 

#### For Rippling Admins:
Rippling admins will be able to access reports through leveraging API keys with correctly defined scopes (Reports Permissions: SOC2 Report). Please note that API keys are for internal usage only and it is against Rippling's Terms of Service to provide your API Key to anyone outside of your organization.

For more information on how to access API keys, please visit [this page](https://developer.rippling.com/docs/rippling-api/docs/Getting-Started/b-Customers.md).

### Step 1: See Available Report Templates
Once you've retrieved the proper authorization from the customer, your application will need to first pull the full list of available report templates and determine the most appropriate reports to access.

To do so, your application can retrieve the available templates using the [Available Report Templates](https://developer.rippling.com/docs/rippling-api/RipplingOpenAPI.v1.yaml/paths/~1reports~1report_templates/get) endpoint.

**Reports Hierarchy:**

| Master Reports                   | Sub-reports                                                                                                                                                                                                                                                                                               |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SOC2    | access_control_report, authentication_settings_report, background_check_candidate_report, background_check_status_report, application_status_report, app_access, performance_management_objective_report, performance_management_pulse_report, performance_management_review_report                                                                                               |
| Insurance     | fsa_enrollment, hsa_enrollment, insurance_enrollment, commuter_enrollment                                                                                                                    |
| Hardware | inventory                                                                                                                         |


<!--
type: tab
title: Request
-->

```js
curl --request GET \
  --url https://api.rippling.com/platform/api/reports/report_templates \
  --header 'authorization: Bearer REDACTED'
```

<!--
type: tab
title: Response
-->
```js
[
  {
    "templateName": "access_control_report",
    "templateID": "access_control_report"
  },
  {
    "templateName": "authentication_settings_report",
    "templateID": "authentication_settings_report"
  },
  {
    "templateName": "application_status_report",
    "templateID": "application_status_report"
  },
  {
    "templateName": "app_access",
    "templateID": "app_access"
  },
  {
    "templateName": "performance_management_objective_report",
    "templateID": "performance_management_objective_report"
  },
  {
    "templateName": "performance_management_pulse_report",
    "templateID": "performance_management_pulse_report"
  },
  {
    "templateName": "performance_management_review_report",
    "templateID": "performance_management_review_report"
  },
  {
    "templateName": "soc2",
    "templateID": "soc2"
  },
  {
    "templateName": "fsa_enrollment",
    "templateID": "fsa_enrollment"
  },
  {
    "templateName": "hsa_enrollment",
    "templateID": "hsa_enrollment"
  },
  {
    "templateName": "insurance_enrollment",
    "templateID": "insurance_enrollment"
  },
  {
    "templateName": "commuter_enrollment",
    "templateID": "commuter_enrollment"
  }
]
```

<!-- type: tab-end -->

### Step 2: Get Report Template Information

Then using the appropriate templateID, you can identify the structure and different fields within the report template using the [Report Template Information](https://developer.rippling.com/docs/rippling-api/RipplingOpenAPI.v1.yaml/paths/~1reports~1%7Breport_template%7D~1report_template_info/get).

<!--
type: tab
title: Request
-->

```js
curl --location --request GET 'https://api.rippling.com/platform/api/reports/soc2/report_template_info' \
--header 'Authorization: Bearer REDACTED'
```

<!--
type: tab
title: Response (soc2)
-->
```js
[
  {
    "templateDisplayName": "Access Control Report",
    "fieldDescriptionMap": {
      "Full Admin": "Is the role a full admin",
      "Hiring and Termination access": "Access to Hiring and Termination",
      "App access": "Access to Apps",
      "Department": "The employee's department. CSV exports will show only the employee's terminal department, however reports in Rippling will show the full department tree (e.g., Sales > Account Executives > Enterprise Sales)",
      "Location": "The employee's work location name, e.g. \"San Fran - HQ\"",
      "Date of birth": "The employee's Date of Birth in MM/DD/YYYY format, e.g. \"01/23/2017\"",
      "Employee": "The employee's full name. Employees with multiple \"jobs\" with your company (for example, as both 1099 and W2, or who were terminated and then re-hired) will have separate records for each job.",
      "Employee ZIP": "The US postal zip code or the pin code for the employee's address, e.g. \"94114\"",
      "Start date": "The employee's first day of employment, e.g. \"01/23/2017\"",
      "Super Admin": "Is the role a super admin",
      "Full name": "The employee's full name, e.g. \"John Doe\"",
      "Can approve payroll run access": "Access to Payroll information"
    },
    "templateName": "access_control_report"
  },
  {
    "templateDisplayName": "Authentication Settings Report",
    "fieldDescriptionMap": {
      "2FA required": "Is two factor authentication required for the company",
      "Name": "Name of the rule",
      "Password minimum length": "The minimum length of characters of password for login",
      "Session timeout(seconds)": "How long before employees are logged out of Rippling, regardless of activity in seconds",
      "2FA timeout(seconds)": "How long before employees are prompted to re-enter 2FA authorization",
      "2FA Method": "The method for enforcing 2FA",
      "Session Inactivity timeout(seconds)": "How long an employee can be inactive before being logged out of Rippling in seconds",
      "Password minimum complex characters": "The minimum length of complex characters password for login",
      "Description": "Description about the settings"
    },
    "templateName": "authentication_settings_report"
  },
  {
    "templateDisplayName": "Application Status Report",
    "fieldDescriptionMap": {
      "API Installation status": "Api integration status for the app",
      "App admins": "Admins of the app",
      "Application Status": "indicates whether the app is installed(completely, incompletely) or not installed",
      "Installed app name": "Name of the installed app",
      "SAML Installation status": "SAML integration status for the app."
    },
    "templateName": "application_status_report"
  },
  {
    "templateDisplayName": "Application provisioning history report",
    "fieldDescriptionMap": {
      "Employee": "The employee's full name. Employees with multiple \"jobs\" with your company (for example, as both 1099 and W2, or who were terminated and then re-hired) will have separate records for each job.",
      "Application": "Application name",
      "Access end": "The date and time the employee's access to the application was revoked",
      "Full name": "The employee's full name, e.g. \"John Doe\"",
      "Access start": "The date and time the employee was granted access to the application"
    },
    "templateName": "app_access"
  }
]
```

<!-- type: tab-end -->


### Step 3: Creating a new report
Once you have determined the most appropriate report to leverage, use the POST Report endpoint to initiate a report creation for either a main or sub-report. For larger organizations, the report may take a few minutes.

<!--
type: tab
title: Request
-->

```js
curl --request POST \
  --url https://api.rippling.com/platform/api/reports/report_data \
  --header 'authorization: Bearer REDACTED' \
  --header 'Content-Type: application/json' \
  --data '{"report_name":"soc2"}'
```

<!--
type: tab
title: Response
-->
```js
{
  "message": "Triggered a job to create Report",
  "request_id": REDACTED
}
```

<!-- type: tab-end -->



### Step 4: Retrieve Report Data
Finally, after the report creation process has been completed, you can leverage the `/report_data` endpoint to retrieve data from the report based on the request ID.

<!--
type: tab
title: Request
-->

```js
curl --request GET \
  --url https://api.rippling.com/platform/api/reports/report_data?request_id={request_id} \
  --header 'authorization: Bearer REDACTED' \

```

<!--
type: tab
title: Response
-->
```js
{
  "Access Control Report": [
    {
      "Full Admin": "Yes",
      "Hiring and Termination access": "All employees",
      "App access": "All apps for all employees",
      "Department": [
        "qyu&juhus"
      ],
      "Location": "San Francisco",
      "Date of birth": "2017-06-08",
      "Employee": "5d6e6ba9fa9c4e5b156a8b06",
      "Employee ZIP": null,
      "Start date": "2019-09-03",
      "Super Admin": "Yes",
      "Full name": "James Smith",
      "Can approve payroll run access": "All employees"
    },
    {
      "Full Admin": "No",
      "Hiring and Termination access": "All employees",
      "App access": "Some apps for some/all employees",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Date of birth": "2006-08-21",
      "Employee": "5fa0213a41455b00285532dd",
      "Employee ZIP": "86549",
      "Start date": null,
      "Super Admin": "No",
      "Full name": "Shavonne Bartoletti",
      "Can approve payroll run access": "No Permission"
    },
    {
      "Full Admin": "No",
      "Hiring and Termination access": "All employees",
      "App access": "All apps for all employees",
      "Department": [
        "Engineering"
      ],
      "Location": "San Francisco",
      "Date of birth": "2018-03-28",
      "Employee": "5fa0213241455b0028552f03",
      "Employee ZIP": "58180",
      "Start date": "2020-10-21",
      "Super Admin": "No",
      "Full name": "Annika McDermott",
      "Can approve payroll run access": "No Permission"
    },
    {
      "Full Admin": "Yes",
      "Hiring and Termination access": "All employees",
      "App access": "All apps for all employees",
      "Department": [
        "Engineering"
      ],
      "Location": "San Francisco",
      "Date of birth": "2017-06-24",
      "Employee": "5d6e6babfa9c4e5b156a8bcb",
      "Employee ZIP": "94110",
      "Start date": "2019-09-03",
      "Super Admin": "Yes",
      "Full name": "Michael Smith",
      "Can approve payroll run access": "All employees"
    },
    {
      "Full Admin": "No",
      "Hiring and Termination access": "Few employees",
      "App access": "Some apps for some/all employees",
      "Department": [
        "When fetching the User from the rippling API  department property of few users is returned empty This is the case when the department has long names"
      ],
      "Location": "India",
      "Date of birth": "2017-06-15",
      "Employee": "5d6e6bacfa9c4e5b156a8c1f",
      "Employee ZIP": null,
      "Start date": "2019-09-03",
      "Super Admin": "No",
      "Full name": "Maria Garcia",
      "Can approve payroll run access": "No Permission"
    },
    {
      "Full Admin": "No",
      "Hiring and Termination access": "No Permission",
      "App access": "Some apps for some/all employees",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Date of birth": "1981-11-21",
      "Employee": "5fa0213141455b0028552e77",
      "Employee ZIP": "26343",
      "Start date": null,
      "Super Admin": "No",
      "Full name": "Jahiem Bernhard",
      "Can approve payroll run access": "No Permission"
    },
    {
      "Full Admin": "No",
      "Hiring and Termination access": "All employees",
      "App access": "All apps for all employees",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Date of birth": "1989-12-01",
      "Employee": "5fa0211f41455b0028552636",
      "Employee ZIP": "58036",
      "Start date": null,
      "Super Admin": "No",
      "Full name": "Doshia Breitenberg",
      "Can approve payroll run access": "No Permission"
    },
    {
      "Full Admin": "Yes",
      "Hiring and Termination access": "All employees",
      "App access": "All apps for all employees",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Date of birth": "1974-04-26",
      "Employee": "5fa0213441455b002855301d",
      "Employee ZIP": "73018",
      "Start date": null,
      "Super Admin": "No",
      "Full name": "Ahmad Bartoletti",
      "Can approve payroll run access": "All employees"
    },
    {
      "Full Admin": "Yes",
      "Hiring and Termination access": "All employees",
      "App access": "All apps for all employees",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Date of birth": "2009-04-17",
      "Employee": "5fa0213341455b0028552f90",
      "Employee ZIP": "59150",
      "Start date": null,
      "Super Admin": "Yes",
      "Full name": "Freeman Cartwright",
      "Can approve payroll run access": "All employees"
    },
    {
      "Date of birth": "1980-03-27",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0213e41455b0028553484",
      "Employee ZIP": "87213",
      "Start date": null,
      "Full name": "Tyreek Zboncak"
    },
    {
      "Date of birth": "1997-09-20",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0213841455b00285531c3",
      "Employee ZIP": "53965",
      "Start date": null,
      "Full name": "Ora Kris"
    },
    {
      "Date of birth": "1993-01-31",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0212341455b0028552868",
      "Employee ZIP": "76453",
      "Start date": null,
      "Full name": "Nolia Wolff"
    },
    {
      "Date of birth": "1986-10-28",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0213c41455b00285533f7",
      "Employee ZIP": "22256",
      "Start date": null,
      "Full name": "Latifah Haley"
    },
    {
      "Date of birth": "1994-01-09",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0212641455b0028552982",
      "Employee ZIP": "36544",
      "Start date": null,
      "Full name": "Meg Spencer"
    },
    {
      "Date of birth": "1990-04-20",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0213641455b0028553136",
      "Employee ZIP": "63073",
      "Start date": null,
      "Full name": "Hayes Lueilwitz"
    },
    {
      "Date of birth": "1995-03-28",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0213941455b0028553250",
      "Employee ZIP": "47745",
      "Start date": null,
      "Full name": "Ines Haag"
    },
    {
      "Date of birth": "2010-11-10",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0212941455b0028552b28",
      "Employee ZIP": "80384",
      "Start date": null,
      "Full name": "Giselle Watsica"
    },
    {
      "Date of birth": "1989-05-26",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0213b41455b002855336a",
      "Employee ZIP": "47932",
      "Start date": null,
      "Full name": "Elfreda Kirlin"
    },
    {
      "Date of birth": "1973-02-17",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0212a41455b0028552bb5",
      "Employee ZIP": "61356",
      "Start date": null,
      "Full name": "Kevan Swaniawski"
    },
    {
      "Date of birth": null,
      "Department": [
        "Sales",
        "SMB"
      ],
      "Location": "India",
      "Employee": "5f6b760383f62a089470d11b",
      "Employee ZIP": null,
      "Start date": "2020-09-23",
      "Full name": "Owel Dsf"
    },
    {
      "Date of birth": "1981-07-01",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0212241455b00285527dc",
      "Employee ZIP": "38648",
      "Start date": null,
      "Full name": "Nyah Schuster"
    },
    {
      "Date of birth": "2017-06-16",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0212b41455b0028552c42",
      "Employee ZIP": "59316",
      "Start date": null,
      "Full name": "Lou Ryan"
    },
    {
      "Date of birth": "2003-10-15",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0212e41455b0028552d5b",
      "Employee ZIP": "94897",
      "Start date": null,
      "Full name": "Durell Haag"
    },
    {
      "Date of birth": "1990-10-21",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0212841455b0028552a9b",
      "Employee ZIP": "32990",
      "Start date": null,
      "Full name": "Aili Prosacco"
    },
    {
      "Date of birth": "2006-03-13",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0212141455b0028552750",
      "Employee ZIP": "88631",
      "Start date": null,
      "Full name": "Gidget Stoltenberg"
    },
    {
      "Date of birth": "1976-05-07",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0212741455b0028552a0e",
      "Employee ZIP": "20956",
      "Start date": null,
      "Full name": "Phyliss Hegmann"
    },
    {
      "Date of birth": "1981-01-03",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0211d41455b00285525aa",
      "Employee ZIP": "12982",
      "Start date": null,
      "Full name": "Devante Bernhard"
    },
    {
      "Date of birth": "1996-05-02",
      "Department": [
        "Engineering"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0213541455b00285530a9",
      "Employee ZIP": "63893",
      "Start date": "2020-11-01",
      "Full name": "Jacki Marquardt"
    },
    {
      "Date of birth": "2017-07-11",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0212041455b00285526c3",
      "Employee ZIP": "94033",
      "Start date": null,
      "Full name": "Kelis Oberbrunner"
    },
    {
      "Date of birth": "2009-02-07",
      "Department": [
        "Engineering"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0211c41455b002855251b",
      "Employee ZIP": "82174",
      "Start date": "2020-11-01",
      "Full name": "Marianne Bahringer"
    },
    {
      "Date of birth": "1970-03-19",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0212d41455b0028552ccf",
      "Employee ZIP": "55166",
      "Start date": null,
      "Full name": "Jeri Hauck"
    },
    {
      "Date of birth": "1981-11-10",
      "Department": [
        "No Department"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0212f41455b0028552de8",
      "Employee ZIP": "12334",
      "Start date": null,
      "Full name": "Terence Hand"
    },
    {
      "Date of birth": "1973-07-02",
      "Department": [
        "Engineering",
        "Infra"
      ],
      "Location": "San Francisco",
      "Employee": "5fa0212541455b00285528f5",
      "Employee ZIP": "72422",
      "Start date": "2020-10-21",
      "Full name": "Edgardo Casper"
    }
  ]
}
```

<!-- type: tab-end -->



## Frequently Asked Questions


### How can I access reports as a Rippling admin?
You are able to access reports via your API key. Make sure the relevant scopes are selected. View API key page for more information.