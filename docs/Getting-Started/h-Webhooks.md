---
tags: [webhook, webhooks]
---

# Webhooks

Rippling Partner Applications have the option to provide a Webhook URL for their application to receive event triggered notifications.

> **Currently, Rippling only supports webhooks in the production environment.**

Rippling will make a POST to the Webhook URL that the partner has provided in their [development package](https://developer.rippling.com/docs/rippling-api/docs/Submit/development-package.md).

The POST will include the following form-encoded parameters.

| Parameter             | Description                                                                                                                                                                                                                                                     |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| event_name            | One of the following events:`employee.created`,  `employee.updated`, `employee.deleted`, `group.updated`, `company.updated`, `company.deleted`, `401_deductions_updated`, `custom_info_field.created`, `custom_info_field.updated`, `custom_info_field.deleted` |
| company_id            | Rippling ID of the company as a string.                                                                                                                                                                                                                         |
| company_primary_email | The email address of the primary company admin as a string.                                                                                                                                                                                                     |
| id                    | Rippling ID of the the employee or group, if applicable.                                                                                                                                                                                                        |

**Sample Webhook**

    event_name=employee.updated&id=5ed540606c9a4e3e61c0d383&company_primary_email=aamir%2Bprod%40rippling.com&company_id=595f75ffd2a5f80ae22ce88e
