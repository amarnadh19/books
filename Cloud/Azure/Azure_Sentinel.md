# What is Azure Sentinel?

Microsoft Azure Sentinel is a scalable, cloud-native, **security information event management (SIEM)** and **security orchestration automated response (SOAR)** solution.

Azure Sentinel delivers intelligent security analytics and threat intelligence across the enterprise, providing a single solution for alert detection


## Azure Sentinel capabilities

Azure Sentinel enables you to:

- **Collect Cloud data at scale**

  Collect data across all users, devices, applications, and infrastructure, both on-premises and from multiple clouds.

- **Detect previously undetected threats**

  Minimize false positives by using Microsoft's comprehensive analytics and threat intelligence.

- **Investigate threats with AI**

  Examine suspicious activities at scale, tapping into years of cybersecurity experience from Microsoft.

- **Respond to incidents rapidly**

  Use built-in orchestration and automation of common tasks.


## Connect your data sources

Azure Sentinel supports a number of sta sources, which it can analyze for security events.

These connections are handled by build-in connectors or industry-standard log formats and APIs.

- **Connect Microsoft solutions**

  Connectors provide real-time integration for services like Microsoft Threat Protection solutions, Microsoft 365 sources, Azure Active Directory and Windows Defender Firewall.

- **Connect other services and solutions**

  Connectors are available for common non-Microsoft services and solutions, including AWS CloudTrail, Citrix Analytics, Sophos XG firewall, VMware Carbon Black Cloud, and Okta SSO.

- **Connect industry-standard data sources**

  Azure Sentinel supports data from other sources that use the Common Event Format (CEF) messaging standard Syslog, or Rest API.


## Detect Threats

**Build in Analytics** use templates designed by MS team of security experts and analysts based on known threats.

**Custom analytics** are rules that you create to search for specific criteria within your environment. You can preview the number of results that the query would generate and set a schedule for the query to run.


## Investigate and respond

When Azure Sentinel detects suspicious events, Tailwind Traders can investigate specific alerts or incidents (a group of related alerts). With the investigation graph, the company can review information from entities directly connected to the alert, and see common exploration queries to help guide the investigation.

The company will also use Azure Monitor Playbooks to automate responses to threats. For example, it can set an alert that looks for malicious IP addresses that access the network and create a workbook

When an admin chooses Block, the IP address is blocked in the firewall, and the user is disabled in Azure Active Directory. When an admin chooses Ignore, the alert is closed in Azure Sentinel, and the incident is closed in the IT ticketing system.

