# Scopes

The beginning of an awesome article...

You will need to provide Rippling with your application scopes. These scopes are transparently displayed to Rippling customer's that choose to install the application.

Scopes           | Description
-----------------|---------------------------------------------------------------------------------------------------------------------------
company          | The parent company scope. This is a prequisite to additional company:* scopes, but does not serve as a scope superset.
employee         | The parent employee scope. This is a prerequisite to additional employee:* scopes, but does not serve as a scope superset.
company:activity | Permission to read information regarding the company's activity.
company:address  | Permission to read the company's address.
company:phone    | Permission to read the company's phone information.