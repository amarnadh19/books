# Azure AD

Azure Active Directory (Azure AD) is Microsoft's multi-tenant cloud-based directory and identity management service.

While they share a similar name, Azure AD is not a cloud version of Windows Server Active Directory. It's also not intended as a complete replacement for an on-premises Active Directory. 

Instead, if you're already using a Windows AD server, you can connect it to Azure AD to extend your directory into Azure. This approach allows users to use the same credentials to access local and cloud-based resources.

Azure Active directory is MS enterprise cloud based identity and Access management (IAM). It can be sync with on-prem AD and Provide authentication to other cloud providers through OAUTH.

![](https://github.com/amarnadh19/books/blob/main/images/az_AD_fun_1.png?)

## Benefits and features

- **Single Sign-on to any cloud or on-premises webapp** --> Azure Active Directory provides secure single sign-on to cloud and on-premises applications. SSO includes Microsoft 365 and thousands of SaaS applications such as Salesforce, Workday, DocuSign, ServiceNow, and Box.

- **Works with iOS, MacOS, Android and Windows devices** --> Users can launch applications from a personalized web-based access panel, mobile app, Microsoft 365, or custom company portals using their existing work credentials.

- **Protect on-premises web applications with secure remote access** --> Access your on-permises web applications from everywhere and protect with multi-factor authentication, conditional access policies, and group based access management. Users can access SaaS and on-premises web apps from the same portal.

- **Easily extend Active Directory to the Cloud** --> You can connect Active Directroy and other on-premises directories to Azure active Directroy in Just a few steps. This connection means a consistent set of users, groups, passwords and devices across both environments.

- **Protect sensitive data and applications** --> You can enhance application access security with unique identiy protection capabilites. This includes a consolidated view into suspicious sign-in activities and potential vulnerabilites. You can also take advantage of advanced security reports, notifications, remediation recommendations, and risk-based policies.

- **Reduce costs and enhance security with self-service capabilities** --> Delegate important tasks such as resetting passwords and the creation and management of groups of your enployees. Providing self-service application access and password management through verification steps can reduce helpdesk calls and enhance security.

## Azure AD concepts

- **Identity** --> An object that can get authenticated. An identity can be a user with a username and password. Identities also include applications or other servers that might require authentication through secret keys or certificates.

- **Account** --> An identity that has data associated with it. You cannot have an account without an identity.

- **Azure AD Account** --> An identity created through Azure AD or another Microsoft cloud service, such as Microsoft 365. Identities are stored in Azure AD and accessible to your organizations's cloud service subscriptions. This account is also sometimes called a Work or School account.

- **Aure Subscription** --> Used to pay for Azure cloud services. You can have many subscriptions and they were linked to a credit card.

- **Azure tenant/directory** --> A dedicated and trusted instance of Azure AD, a Tenant is automatically created when your organization signs up for a MS cloud service subscription.

  - More instances of Azure AD can be created.
  - Azure AD is the underlying product providing the identity service.
  - The term Tenant means a single instance of Azure AD representing a single organization.
  - The terms Tenant and Directory are often used interchangeably.


## Compare AD DS to Azure Active Directory

AD DS is the traditional deployment of Windows Server-based Active Directory on a physical or virtual server.

## Azure AD is different from AD DS

Although Azure AD has many similarities to AD DS, there are also many differences. It is important to realize that using Azure AD is different from deploying an AD domain Controller on an Azure virtual machine  and adding it to your on-premises domain.

Here are some characteristics of Azure AD that make it different.

  - **Identity solution** --> Azure AD is primarily an identity solution, and it is designed for Internet based applications by using HTTP and HTTPS communications. 

  - **Rest API Querying** --> Because Azure AD is HTTP/HTTPS based, it cannot be queried through LDP. Instead, Azure AD used the REST API over HTTP and HTTPS.

  - **Communication Protocols** --> Because Azure AD is HTTP/HTTPS based, it does not use Kerberos authentiation. Instead, it uses HTTP and HTTPS protocols such as SAML, WS-Federation, and OpenID Connect for authentication.

  - **Federation Services** --> Azure AD includes federation services, and many third party services (such as Facebook).

  - **Flat structure** --> Azure AD users and groups are created in a flat structure, and there are no Organizational Units (OUs) or Group Policy Objects (GPOs).

## Select Azure Active Directory Editions

Azure Active Directory comes in four editions—Free, Microsoft 365 Apps, Premium P1, and Premium P2. The Premium editions are available through a Microsoft Enterprise Agreement, the Open Volume License Program, and the Cloud Solution Providers program. Azure and Microsoft 365 subscribers can also buy Azure Active Directory Premium P1 and P2 online.

- **Azure Active Directory Free** --> Provides user and group management, on-premises directory synchronization, basic reports, and single sign-on across Azure, Microsoft 365, and many popular SaaS apps.

- **Azure Active Directory Microsoft 365 Apps** --> This edition is included with O365. In addition to the Free features, this edition provides Identity & Access Management for Microsoft 365 apps including branding, MFA, group access management, and self-service password reset for cloud users.

- **Azure Active Directory Premium P1** --> In addition to the Free features, P1 also lets your hybrid users access both on-premises and cloud resources. It also supports advanced administration, such as dynamic groups, self-service group management, Microsoft Identity Manager (an on-premises identity and access management suite) and cloud write-back capabilities, which allow self-service password reset for your on-premises users.

- **Azure Active Directory Premium P2** --> In addition to the Free and P1 features, P2 also offers Azure Active Directory Identity Protection to help provide risk-based Conditional Access to your apps and critical company data. Privileged Identity Management is included to help discover, restrict, and monitor administrators and their access to resources and to provide just-in-time access when needed.


## Directories, subscriptions, and users

Microsoft offers several cloud-based offerings today - all of which can use Azure AD to identify users and control access.

- Microsoft Azure
- Microsoft 365
- Microsoft Intune
- Microsoft Dynamics 365

When a company or organization signs up to use one of these offerings, they are assigned a default directory, an instance of Azure AD. This directory holds the users and groups that will have access to each of the services the company has purchased. This default directory can be referred to as a *tenant*. A tenant represents the organization and the default directory assigned to it.

*Subscriptions* in Azure are both a billing entity and a security boundary. Resources such as virtual machines, websites, and databases are associated with a single subscription. Each subscription also has a single account owner responsible for any charges incurred by resources in that subscription. If your organization wants a subscription billed to another account, you can transfer the subscription. A subscription is associated with a single Azure AD directory. Multiple subscriptions can trust the same directory, but a subscription can only trust one directory.

Users and groups can be added to multiple subscriptions - this allows the user to create, control, and access resources in the subscription. When you add a user to a subscription, the user must be known to the associated directory as shown in the following image.

![](https://github.com/amarnadh19/books/blob/main/images/az_AD_fun_2.png?)

If you belong to multiple directories, you can switch the current directory you are working in through the Directory + subscription button in the Azure portal header.

![](https://github.com/amarnadh19/books/blob/main/images/az_AD_fun_3.png?)