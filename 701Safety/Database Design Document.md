# 701Safety Database Design Document
### Tables
> Unless otherwise stated, the primary key of tables is assumed to be a GUID

##### Login
*users* : Username, Password hashes, contact information.
*roles* : Role name, Description
*permissions* : Specific Permissions, Descriptions
*role_permissions* : Combination table of Roles and Permissions, PK is combination of role and permission GUID
*user_role* : Combination table of Users and Roles, PK is combination of user and role GUID

---
##### Equipment Inspections
*eqpt_inspection_items* : Specific questions