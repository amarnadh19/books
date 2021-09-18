# Azure Alerts

Alerts proactively notify you when issues are found with your infrastructure or application using your monitoring data in Azure Monitor. They allow you to identify and address issues before the users of your system notice them.

## Monitoring Alerts

Alerting is now available with Azure Monitor.

![](https://github.com/amarnadh19/books/blob/main/images/Az_alert_1.png?)

The Monitor Alerts experience has many benefits.

- **Better notification system**. All newer alerts use action groups, which are named groups of notifications and actions that can be reused in multiple alerts.

- **A unified authoring experience**. All alert creation for metrics, logs and activity log across Azure Monitor, Log Analytics, and Application Insights is in one place.

- **View Log Analytics alerts in Azure portal**. You can now also see Log Analytics alerts in your subscription. Previously these were in a separate portal.

- **Separation of Fired Alerts and Alert Rules**. Alert Rules (the definition of the condition that triggers an alert), and Fired Alerts (an instance of the alert rule firing) are differentiated, so the operational and configuration views are separated.

- **Better workflow**. The new alerts authoring experience guides the user along the process of configuring an alert rule, which makes it simpler to discover the right things to get alerted on.


## Creating Alerts

![](https://github.com/amarnadh19/books/blob/main/images/Az_alert_2.png?)

Alert rules are separated from alerts and the actions taken when an alert fires. The alert rule captures the target and criteria for alerting. The alert rule can be in an enabled or a disabled state. Alerts only fire when enabled.

The following are key attributes of an alert rule:

**Target Resource** - Defines the scope and signals available for alerting. A target can be any Azure resource. Example targets:

- Virtual machines.
- Storage accounts.
- Log Analytics workspace.
- Application Insights.

**Signal** - Emitted by the target resource. Signals can be of the following types: metric, activity log, Application Insights, and log.

**Criteria** - A combination of signal and logic applied on a target resource. Examples:

- Percentage CPU > 70%
- Server Response Time > 4 ms
- Result count of a log query > 100

**Alert Name** - A specific name for the alert rule configured by the user.

**Alert Description** - A description for the alert rule configured by the user.

**Severity** - The severity of the alert after the criteria specified in the alert rule is met. Severity can range from 0 to 4.

- Sev 0 = Critical
- Sev 1 = Error
- Sev 2 = Warning
- Sev 3 = Informational
- Sev 4 = Verbose

**Action** - A specific action taken when the alert is fired. For more information.


### Alert Rules

Creating an alert is a three-step task: define the alert condition, define alert details, and define an action group.

## Action Rules

An action group is a collection of notification preferences defined by the owner of an Azure subscription. Azure Monitor and Service Health alerts use action groups to notify users that an alert has been triggered. Various alerts may use the same action group or different action groups depending on the user's requirements.

When an action is configured to notify a person by email or SMS the person will receive a confirmation indicating he / she has been added to the action group.

![](https://github.com/amarnadh19/books/blob/main/images/Az_alert_3.png?)

- Email – Emails will be sent to the email addresses. Ensure that your email filtering is configured appropriately. You may have up to 1000 email actions in an Action Group.

- ITSM – You may have up to 10 ITSM actions in an Action Group ITSM Action requires an ITSM Connection.

- Logic App – You may have up to 10 Logic App actions in an Action Group.

- Function App – The function keys for Function Apps configured as actions are read through the Functions API.

- Runbook – You may have up to 10 Runbook actions in an Action Group.

- SMS – You may have up to 10 SMS actions in an Action Group.

- Voice – You may have up to 10 Voice actions in an Action Group.

- Webhook – You may have up to 10 Webhook actions in an Action Group. Retry logic - The timeout period for a response is 10 seconds. The webhook call will be retried a maximum of 2 times when the following HTTP status codes are returned: 408, 429, 503, 504 or the HTTP endpoint does not respond. The first retry happens after 10 seconds. The second and last retry happens after 100 seconds.

You may have up to 10 Azure app actions in an Action Group. At this time the Azure app action only supports ServiceHealth alerts.

## Managing Alerts

You can alert on metrics and logs as described in monitoring data sources. These include but are not limited to:

- Metric values

- Log search queries

- Activity Log events

- Health of the underlying Azure platform

- Tests for web site availability

## Alerts Experience

The default Alerts page provides a summary of alerts that are created within a particular time window. It displays the total alerts for each severity with columns that identify the total number of alerts in each state for each severity.

![](https://github.com/amarnadh19/books/blob/main/images/Az_alert_4.png?)

### Subscription
	
Select up to five Azure subscriptions. Only alerts in the selected subscriptions are included in the view.

### ResourceGroup

Select a single resource group. Only alerts with targets in the selected resource group are included in the view.

### Time Range

Only alerts fired within the selected time window are included in the view. Supported values are the past hour, the past 24 hours, the past 7 days, and the past 30 days.

## Alert Detail Page

The Alert detail page is displayed when you select an alert. It provides details of the alert and enables you to change its state.

![](https://github.com/amarnadh19/books/blob/main/images/Az_alert_5.png?)

