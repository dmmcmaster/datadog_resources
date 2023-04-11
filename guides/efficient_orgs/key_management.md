# Key Management

## Basics
- In respect to the Datadog ecosystem, keys play a very different role whether we're talking about Agent deployments versus scripts and API usage. For this reason we will break things down between API Keys and APP Keys. We will focus on key management specifically, separate from RBAC or Auditing concerns which play a role in larger organizational strategy and security.


> \* __NOTE:__ I will focus solely on key management best practices on this page. Datadog does have tools like Audit Trail which allow you to create audit reports, dashboards, etc. I may create a follow-up page on key, product usage, and other type of auditing in the future.


----
## API KEYS

- An API Key is the minimum requirement to have an agent submit telemetry to Datadog. Most best practices I will outline in this section will be less focused on Datadog specifically and more on Enterprise standards. Your organization's IT, Security, or other team may have requirements around keys and password already so please defer to those.

## 1. Separation of concerns
- This is a fancy phrase that just refers to making sure the key has a purpose and that not every app, team, or other logical business unit uses a single key. This is especially critical when going through a migration or operating on a different set of requirements (for example, one team may be focused on customer facing apps and the other on peripheral tooling).

## 2. Key Rotation
- As a security best practice it is recommended to rotate keys on a regular basis. This is easy enough to sync up with a new version of your product being released, an annual security audit, etc.

----
## APPLICATION KEYS

- If you've made it this far, this is where things heat up! App keys work in conjunction with API keys. APP keys play no part in the agent deployments. If you would like to scope configurations or capabilities in the agent you would defer to the agent configuration and not permissions on the key. APP keys come into play when automating deployment using an infrastructure as code tool or interacting with Datadog's customer-facing API.

## 1. Service Accounts
- Service accounts allow APP keys to be created under them. These keys inherit the permissions of the service account. Therefore, it makes it a lot simpler to have fully locked down "roles" or service accounts for one purpose like strictly log submission or data warehousing. While APP keys do have the ability to be scoped it is easier to manage in a service account. It is also more effective to alert off of app key audit events since service accounts are tied to an email.
    
    - [Documentation Link](https://docs.datadoghq.com/account_management/org_settings/service_accounts/#overview)

## 2. Scope the Keys
- Application keys do have the ability to be scoped. This is ok for existing keys or ad hoc tasks but for longer standing or repetitive tasks I would recommend service accounts.
    - [Documentation Link](https://docs.datadoghq.com/account_management/api-app-keys/#scopes)