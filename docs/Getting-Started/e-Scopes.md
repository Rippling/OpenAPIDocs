---
tags: [scope, scopes]
---

# Scopes

Rippling Application Partners are required to explicitly provide Rippling with their necessary authorization scopes in the [Rippling development package](https://developer.rippling.com/docs/rippling-api/docs/Submit/development-package.md). These scopes are transparently displayed to Rippling customers during the installation process to ensure the transparent authorization of access to their company's information.

Please note, for scopes enabling access to a company's fields, the ability to update that field will be dependent on the endpoints available. Please see the API documentation for more information on how integrations can manipulate Rippling fields.

_Additionally, you may notice that certain fields are not marked as required the Rippling API documentation. The information returned via these requests will be determined by the level of scopes your access token or API key is entitled to access._

| Scope                                  | Description                                                                                                                                                |
|----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| company                                | The parent company scope. This is a prequisite to any additional company:\* scopes, but does not serve as a scope superset.                                |
| employee                               | The parent employee scope. This is a prerequisite to any additional employee:\* scopes, but does not serve as a scope superset.                            |
| company:activity                       | Permission to access information regarding the company's activity.                                                                                         |
| company:address                        | Permission to access the company's address.                                                                                                                |
| company:phone                          | Permission to access the company's phone information.                                                                                                      |
| company:payschedules                   | Permission to access the company's pay schedule information.                                                                                               |
| company:ein                            | Permission to access the company's EIN information.                                                                                                        |
| company:bankaccounts                   | Permission to access the company's bank account information.                                                                                               |
| company:tax_info                       | Permission to access the company's tax information.                                                                                                        |
| company:payroll_settings               | Permission to access the company's payroll settings.                                                                                                       |
| company:departments                    | Permission to access the company's departments.                                                                                                            |
| company:levels                         | Permission to access the company's levels.                                                                                                                 |
| company:customFields                   | Permission to access the company's custom fields.                                                                                                          |
| company:workLocations                  | Permission to access the company's work locations.                                                                                                         |
| company:subscription                   | Permission to access the company's Rippling subscription.                                                                                                  |
| company:leave_requests                 | Permission to access the company's leave request information.                                                                                              |
| company:company_deductions             | Permission to access the company's deductions.                                                                                                             |
| company:employee_deductions            | Permission to access the company's employees' departments.                                                                                                 |
| admin:name                             | Permission to access the company's admins' names.                                                                                                          |
| admin:personalEmail                    | Permission to access the company's admins' personal emails.                                                                                                |
| admin:phone                            | Permission to access the company's admins' phone number.                                                                                                   |
| admin:workEmail                        | Permission to access the company's admins' work emails.                                                                                                    |
| admin:roleState                        | Permission to access the company's admins' role states.                                                                                                    |
| admin:department                       | Permission to access the company's admins' departments.                                                                                                    |
| admin:workLocation                     | Permission to access the company's admins' work location.                                                                                                  |
| employee:name                          | Permission to access the company's employees' names.                                                                                                       |
| employee:ssn                           | Permission to access the company's employees' social security numbers.                                                                                     |
| employee:employmentType                | Permission to access the company's employees' employment types.                                                                                            |
| employee:dob                           | Permission to access the company's employees' date of births.                                                                                              |
| employee:address                       | Permission to access the company's employees' addresses.                                                                                                   |
| employee:personalEmail                 | Permission to access the company's employees' personal emails.                                                                                             |
| employee:phone                         | Permission to access the company's employees' phone numbers.                                                                                               |
| employee:filingStatus                  | Permission to access the company's employees' filing statuses.                                                                                             |
| employee:workEmail                     | Permission to access the company's employees' work emails.                                                                                                 |
| employee:title                         | Permission to access the company's employees' titles.                                                                                                      |
| employee:startDate                     | Permission to access the company's employees' start dates.                                                                                                 |
| employee:w2StartDate                     | Permission to access the company's employees' w2 start dates.                                                                                             |
| employee:endDate                       | Permission to access the company's employees' end dates.                                                                                                   |
| employee:roleState                     | Permission to access the company's employees' role states.                                                                                                 |
| employee:compensation                  | Permission to access the company's employees' compensations.                                                                                               |
| employee:flsaStatus                    | Permission to access the company's employees' FLSA exempt and non-exempt statuses.                                                                         |
| employee:department                    | Permission to access the company's employees' department.                                                                                                  |
| employee:level                         | Permission to access the company's employees' levels.                                                                                                      |
| employee:manager                       | Permission to access the company's employees' managers.                                                                                                    |
| employee:departmentId:write            | Permission to access to the company's employees' departments.                                                                                              |
| employee:workLocation                  | Permission to access the company's employees' work locations.                                                                                              |
| employee:payroll                       | Permission to access the company's employees' payroll information.                                                                                         |
| employee:customFields                  | Permission to access the company's employees' custom field information.                                                                                    |
| employee:isLeaseEmployee               | Permission to access the company's employees' lease status information.                                                                                    |
| employee:customFields:write            | Permission to write to the company's employees' custom fields information.                                                                                 |
| employee:hasCompatiblePlanStatus       | Permission to access fields relating to whether the company's employees' have compatible plan statuses.                                                    |
| employee:gender                        | Permission to read the company's employees' gender information.                                                                                            |
| employee:identifiedGender              | Permission to read the company's employees' identified gender information.                                                                                 |
| employee:photo              | Permission to access the company's employees' photo.                                                                                                        |
| employee:smallPhoto              | Permission to access the company's employees' photo                                                                                              |
| groups:read                            | Permission to read the company's group information.                                                                                                        |
| groups:write                           | Permission to write to the company's group information.                                                                                                    |
| group_members:read                     | Permission to read the company's group membership information.                                                                                             |
| group_members:write                    | Permission to write to the company's group membership information.                                                                                         |
| deduction:\_401K                       | Permission to access the company's 401k information.                                                                                                       |
| deduction:ROTH_401K                    | Permission to access the Roth 401k information.                                                                                                            |
| deduction:\_401K_LOAN_PAYMENT          | Permission to access 401k loan payment deductions information.                                                                                             |
| deduction:HSA                          | Permission to access HSA deductions information.                                                                                                           |
| deduction:STUDENT_LOAN                 | Permission to access the student loan deductions information.                                                                                              |
| deduction:CUSTOM_TAXABLE               | Permission to access the student loan deductions information.                                                                                              |
| saml:idp_metadata                      | Permission to access the current company's SAML metadata information.                                                                                      |
| ats:candidates                         | Permission to push ATS candidates to Rippling for onboarding. Please note, this scope is only available to Rippling application developers using OAuth2.0. |
| company:teams                          | Permission to access the company's list of teams.                                                                                                          |
| app:read                               | Permission to read the list of the company's installed applications, as well as information on the user account mapping within those applications.         |
| reports:soc2                           | Permission to read the organization's SOC2 information. Please note, this includes access to the following reports, if applicable to the company: access_control_report, authentication_settings_report, background_check_candidate_report, background_check_status_report, application_status_report, app_access, performance_management_objective_report, performance_management_pulse_report, performance_management_review_report                                        |
| reports:insurance              | Permission to read the organization's insurance report information. Please note, this includes access to the following reports, if applicable to the company: fsa_enrollment, hsa_enrollment, insurance_enrollment, commuter_enrollment                                                                                          |
| reports:hardware              | Permission to read the organization's insurance report information. Please note, this includes access to the following reports, if applicable to the company: inventory                                                                                         |