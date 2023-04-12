# Monitors and SLOs

## Basics
- Monitors and SLOs are one of the most important parts of Datadog and a crucial part of making sure we can act upon anomalies or things going wrong in your environment. Keeping these resources clean and organized provide confidence that you have full coverage across all of your services.

----

## 1. Add Tags
- Like dashboards, I think it can be very helpful to have a common naming schema like `[team name] Cpu alert monitor`, however, you have the ability to add tags which make sorting and filtering much more consistent and actually strengthen the correlation across your telemetry. Adding a `service` tag, for example, will show up in the service health in APM and in the Service Catalog. Customer also have the ability via the Monitor Settings Page to require all new monitors have tags added to them.
    
    - [Documentation Link](https://docs.datadoghq.com/monitors/settings/#overview)
    - [In App Link to Require Tags on Monitors](https://app.datadoghq.com/monitors/settings/policies)

## 2. Muted Monitors
- It is common to schedule a downtime or mute for a maintenance window or deployment to make sure the alerts pointed at that service to not flap or create a false alert. It is also common, from my experience, to spin up test monitors, mute something infinitely, etc. and forget about them or not need them anymore.
- In the manage monitors UI page, you have the ability to filter monitors that have been muted for X number of days. Each user has the ability to set how long they deem to be long enough to consider that monitor outdated or able to delete. I would recommend starting with 30 days as a good starting point but an aggressive approach would be 7 days or more of being muted.

    - [Muted Elapsed Documentation](https://docs.datadoghq.com/monitors/manage/search/#attributes)
    
    
    ![UI Screehshot](https://github.com/dmmcmaster/datadog_resources/blob/main/guides/efficient_orgs/img/monitors/monitor_elapsed.jpg)

## 3. No Notification Channels
- One of the easiest ways to identify monitors to clean up or edit is to search for those without a notification channel. By using the simple query `-notification:*` you can see any monitor that alerts to nowhere. Either add a notification recipient(s) or delete them.

## 4. `NO DATA` Statuses
- When used correctly, the `no data` condition in a monitor can be used to show a container, server, or other resource stopped reporting in and is likely unhealthy. `No Data` can also mean that the scope of the monitor is no longer a viable scope (rename an environment but have the tag on the monitor, spin down your dev environment, etc). You can filter those monitors or SLOs in a no data state and then delete the ones who have been that way for longer than an acceptable period of time.