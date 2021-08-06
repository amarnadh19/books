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

