# Dashboards

## Basics
- Favorited Dashboards are on a user level not the organization level. Feel free to favorite as many as you'd like.

- Create dashboard lists for any logical separation in your company like business unit, team, or product.

- Enable notifications on your dashboards to create audit events when someone edits, deletes, etc.

----

## 1. Create standardized naming schema
- Some ideas include the following:

    - `[TEAM NAME] Dashboard name`
    - `[Env][Team/Product] Dashboard name`
        
        - Note: this should be accomplished using tags and template variables but some customers prefer to monitor different metrics in different environments

## 2. Power Packs
- The most successful organizations I have interacted with have a standard set of metrics or KPIs. To accomplish this into a dashboard, users can create Datadog Power Packs to create a set of standard widgets that visualize these KPIs for applications or environment.
    
    - [Docuentation Link](https://docs.datadoghq.com/dashboards/guide/powerpacks-best-practices/#build-self-explanatory-content)

## 3. Templated Dashboards
- Dashboards are JSON objects behind the scenes. Users can export the JSON in the UI or pull it out of the API and store it in version control or an infrastructure as code tool like Terraform.

    - [Documentation Link](https://docs.datadoghq.com/getting_started/dashboards/#create-multiple-dashboards-quickly)

- Create a standard dashboard, for example `[TEMPLATE] SRE Troubleshooting Dashboard` and restrict editing rights. Instruct Teams onboarding to Datadog to clone this dashboard and create their own version of it.