# Cloud Resources

## Basics
- In most scenarios, when you integrate a cloud account into Datadog, we will look to pull in metrics from all resources in that account. There are some slight variations in approach depending on what cloud provider(s) you are using mainly due to the APIs and levers each CSP allows us to hook into. 

----

## __AWS__

## 1. Account Tags
- There are many ways to add tags on your resources at various stages your templating out configurations or deploying applications. If there are any tags you would use for chargeback or dashboarding for all resources in an AWS account (like business unit, chargeback code, etc) you can add those directly into the integration. This way, app teams can add tags that are meaningful to them on the resources but all metrics will still be enriched with these integration level tags.
    
    - [Documentation Link](https://docs.datadoghq.com/integrations/amazon_web_services/#tags)

## 2. Limit Metric Collection
- Along the theme of tags, you can also add tags to exclude certain resources within an account from being collected. I personally find it easier to do an exclusion (only collect if it does not have team:web tag - "!team:web") instead of an inclusion (collect if has tag team:web - "team:web") UNLESS you are a new Datadog user onboarding and have the ability to set a standard from the beginning. Be advised as well that not all AWS resources are billable so excluding them would not change costs.
    - [Documentation Link](https://docs.datadoghq.com/account_management/billing/aws/#aws-resource-exclusion)

## 2. Limit Regional Collection
- The AWS Integration also allows you to choose specific regions to monitor directly in the UI. This can be enabled and disabled on-the-fly in the integration tile making it easy to scale up and make sure you're only collecting the resources you are interested in.
    - [Documentation Link](https://docs.datadoghq.com/account_management/billing/aws/#aws-resource-exclusion)

----

## __AZURE__

## 1. Limit Metric Collection
- Along the theme of tags, you can also add tags to exclude certain resources within an account from being collected. I personally find it easier to do an exclusion (only collect if it does not have team:web tag - "!team:web") instead of an inclusion (collect if has tag team:web - "team:web") UNLESS you are a new Datadog user onboarding and have the ability to set a standard from the beginning. Be advised as well that not all Azure resources are billable so excluding them would not change costs. In the Azure integration, you can do this by hosts and/or App Service Plans
    
    - [Documentation Link](https://docs.datadoghq.com/account_management/billing/azure/#azure-vm-exclusion)


----

## __GCP__

## 1. Limit Metric Collection
- Along the theme of tags, you can also add tags to exclude certain resources within an account from being collected. I personally find it easier to do an exclusion (only collect if it does not have team:web tag - "!team:web") instead of an inclusion (collect if has tag team:web - "team:web") UNLESS you are a new Datadog user onboarding and have the ability to set a standard from the beginning. Be advised as well that not all GCP resources are billable so excluding them would not change costs.
    
    - [Documentation Link](https://docs.datadoghq.com/account_management/billing/google_cloud/#google-cloud-metric-exclusion)