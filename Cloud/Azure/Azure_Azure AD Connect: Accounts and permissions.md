# Accounts used for Azure AD Connect

![](https://github.com/amarnadh19/books/blob/main/images/Az_adconnect_account_permission_1.png?)

Azure AD Connect uses 3 accounts in order to synchronize information from on-premises or Windows Server Active Directory to Azure Active Directory. These accounts are:

**AD DS Connector account:** used to read/write information to Windows Server Active Directory

**ADSync service account:** used to run the synchronization service and access the SQL database

**Azure AD Connector account:** used to write information to Azure AD.

In addition to these three accounts used to run Azure AD Connect, you will also need the following additional accounts to install Azure AD Connect. These are:

**Local Administrator account:** The administrator who is installing Azure AD Connect and who has local Administrator permissions on the machine.

**AD DS Enterprise Administrator account:** Optionally used to create the “AD DS Connector account” above.

**Azure AD Global Administrator account:** used to create the Azure AD Connector account and configure Azure AD. You can view global administrator accounts in the Azure portal. See List Azure AD role assignments.

**SQL SA account (optional):** used to create the ADSync database when using the full version of SQL Server. This SQL Server may be local or remote to the Azure AD Connect installation. This account may be the same account as the Enterprise Administrator. Provisioning the database can now be performed out of band by the SQL administrator and then installed by the Azure AD Connect administrator with database owner rights.

---

# Installing Azure AD Connect

The Azure AD Connect installation wizard offers two different paths:

- In Express Settings, the wizard requires more privileges. This is so that it can set up your configuration easily, without requiring you to create users or configure permissions.

- In Custom Settings, the wizard offers you more choices and options. However, there are some situations in which you need to ensure you have the correct permissions yourself.


## Express settings installation

In Express settings, the installation wizard asks for the following:

- AD DS Enterprise Administrator credentials

- Azure AD Global Administrator credentials


### AD DS Enterprise Admin credentials

The AD DS Enterprise Admin account is used to configure your on-premises Active Directory. These credentials are only used during the installation and are not used after the installation has completed. The Enterprise Admin, not the Domain Admin should make sure the permissions in Active Directory can be set in all domains.


### Azure AD Global Admin credentials

These credentials are only used during the installation and are not used after the installation has completed. It is used to create the Azure AD Connector account used for synchronizing changes to Azure AD. The account also enables sync as a feature in Azure AD.

### AD DS Connector account required permissions for express settings

The AD DS Connector account is created for reading and writing to Windows Server AD

| Wizard Page | Credentials Collected | Permissions Required | Used For|
| ----------| ----------| --------- | --------|
| N/A | User running the installation Wizard | Administrator of the local server | Creates the ADSync service account that is used as to run the syncronization service. |
| Connect to Azure AD | Azure AD directory credentials | Global Administrator role in Azure AD | Enabling sync in the Azure AD directory;; Creation of the Azure AD connector account is is used for on going sync opreation in Azure AD |
|connect o ADDS| On premises Active Directory credentials | Member of the Enterprise Admins group in Active Directory | Creates the AD DS connector account in Active Directory and grant permissions to it.|

