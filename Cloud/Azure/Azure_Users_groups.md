# Create and Manage users

Every user who needs access to Azure resources needs an Azure user account. A user account contains all the information needed to authenticate you during the sign-in process. Once authenticated, Azure AD builds an access token to authorize you, and determine what resources you can access, and what you can do with those resources.

You use the **Azure Active Directory dashboard** in the Azure portal to work with user objects. Keep in mind that you can only work with a single directory at a time - but you can use the Directory + Subscription pane to switch directories. The dashboard also has a Switch directory button in the toolbar which makes it easy to switch to another available directory.


## View Users

To view the Azure AD users, in the left menu pane, under **Manage**, select **Users**. The **All Users** pane appears. Take a minute to access the portal and view your users. Notice the **User type and Identity issuer** columns, as shown in the following screenshot.

![](https://github.com/amarnadh19/books/blob/main/images/az_ad_users_1.png?)

Typically, Azure AD defines users in three ways:

   - **Cloud identities** - These users exist only in Azure AD. 

   Examples are administrator accounts and users that you manage yourself. Their source is **Azure Active Directory or External Azure Active Directory** if the user is defined in another Azure AD instance but needs access to subscription resources controlled by this directory. When these accounts are removed from the primary directory, they are deleted.

   - **Directory-synchronized identities** - These users exist in an on-premises Active Directory. A synchronization activity that occurs via **Azure AD Connect** brings these users in to Azure. Their source is Windows Server AD.

   - **Guest users** - These users exist outside Azure. 

   Examples are accounts from other cloud providers and Microsoft accounts, such as an Xbox LIVE account. Their source is **Invited user**. This type of account is useful when external vendors or contractors need access to your Azure resources. Once their help is no longer necessary, you can remove the account and all of their access.


## Add users

You can add cloud identities to Azure AD in multiple ways:

- Syncing an on-premises Windows Server Active Directory
- Using the Azure portal
- Using the command line
- Other options

### Sync an on-premises Windows Server Active Directory

**Azure AD Connect** is a separate service that allows you to synchronize a traditional Active Directory with your Azure AD instance. This is how most enterprise customers add users to the directory. The advantage to this approach is users can use **single sign-on (SSO)** to access local and cloud-based resources.

### Use the Azure Portal

You can manually add new users through the Azure portal. This is the easiest way to add a small set of users. You need to be in the User Administrator role to perform this function.

1) To add a new user with the Azure portal, in the top menu bar, select New user.

![](https://github.com/amarnadh19/books/blob/main/images/az_ad_users_2.png?)

2) In addition to Name and User name, you can add profile information, like Job Title and Department.

![](https://github.com/amarnadh19/books/blob/main/images/az_ad_users_3.png?)

3) You can also invite a user into the directory. In this case, an email is sent to a known email address and an account is created and associated with that email address if they accept the invitation.

![](https://github.com/amarnadh19/books/blob/main/images/az_ad_users_4.png?)

The invited user will need to create an associated Microsoft account (MSA) if that specific email address isn't associated with one and the account will be added to the Azure AD as a guest user.


### Use the Command Line

If you have a lot of users to add, a better option is to use a command-line tool. You can run the ```New-AzureADUser``` Azure PowerShell command to add cloud-based users.

```
# Create a password object
$PasswordProfile = New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile

# Assign the password
$PasswordProfile.Password = "<Password>"

# Create the new user
New-AzureADUser -AccountEnabled $True -DisplayName "Abby Brown" -PasswordProfile $PasswordProfile -MailNickName "AbbyB" -UserPrincipalName "AbbyB@contoso.com"

```

The command will return the new user object you created.

```
ObjectId                             DisplayName UserPrincipalName UserType
--------                             ----------- ----------------- --------
f36634c8-8a93-4909-9248-0845548bc515 Abby Brown  AbbyB@contoso.com Member

```

If you prefer a more traditional command-line, you can use the Azure CLI:

```
az ad user create --display-name "Abby Brown" \
                  --password "<password>" \
                  --user-principal-name "AbbyB@contoso.com" \
                  --force-change-password-next-login true \
                  --mail-nickname "AbbyB"

```

Command-line tools allow you to add users in bulk through scripting. The most common approach for this is to use a comma-separated values (CSV) file. You can either manually create this file or export the file from an existing data source.

If you're planning to use a CSV, here are some things to think about:

   - **Naming conventions.** Establish or implement a naming convention for usernames, display names, and aliases. For example, a username might consist of the last name, followed by a period (.), followed by the first name—for example, Smith.John@contoso.com.

   - **Passwords.** Implement a convention for the initial password of a newly created user. Determine how new users will receive their passwords in a security-enhanced way. A commonly used method is generating a random password and then emailing it to the new user or their manager.

To use a CSV with Azure PowerShell:

- Run the ```Connect-AzureAD``` command to create an Azure PowerShell connection to your directory. Connect with an admin account that has privileges on your directory.

- Create new password profiles for the new users. The passwords for the new users need to conform to the password complexity rules you have set for your directory.

- Use ```Import-CSV``` to import the CSV. You need to specify the path and file name of the CSV.

- Loop through the users in the file, constructing the user parameters needed for each user. Example parameters are User Principal Name, Display Name, Given Name, Department, and Job Title.

- Run the ```New-AzureADUser``` command to create each user. Be sure to enable each account.


### Other options

You can also add users to Azure AD programmatically using the Azure AD Graph API, or through the Microsoft 365 Admin Center, and the Microsoft Intune Admin console if you are sharing the same directory.

---

# Create and manage groups

An Azure AD group helps organize users making it easier to manage permissions.

Azure AD allows you to define two different types of groups.

- **Security groups**. These are the most common and are used to manage member and computer access to shared resources for a group of users. For example, you can create a security group for a specific security policy. By doing it this way, you can give a set of permissions to all the members at once, instead of having to add permissions to each member individually. This option requires an Azure AD administrator.

- **Microsoft 365 groups**. These groups provide collaboration opportunities by giving members access to a shared mailbox, calendar, files, SharePoint site, and more. This option also lets you give people outside of your organization access to the group. This option is available to users as well as admins.


## View available groups

You can view all groups by selecting Groups under the Manage section from the Azure AD dashboard. A new Azure AD install won't have any groups defined.

![](https://github.com/amarnadh19/books/blob/main/images/az_ad_users_5.png?)


## Add groups to Azure AD

The same options are available to create groups in Azure AD as we saw with users. The Azure portal is the easiest way to create groups. You must select the group type (Security or Microsoft 365), assign a unique group name, description and a membership type.

![](https://github.com/amarnadh19/books/blob/main/images/az_ad_users_6.png?)

The membership type field can be one of three values:

- **Assigned (static)**. The group will contain specific users or groups that you select.

- **Dynamic user**. You create rules based on characteristics to enable attribute-based dynamic memberships for groups. For example, if a user’s department is Sales, that user will be dynamically assigned to the Sales group. You can set up a rule for dynamic membership on security groups or on Microsoft 365 groups. If the user's department changes in the future, they are automatically removed from the group. This feature requires an Azure AD Premium P1 license.

- **Dynamic device**. You create rules based on characteristics to enable attribute-based dynamic memberships for groups. For example, if a user’s device is associated with the Service department, that device will be dynamically assigned to the Service group. You can set up a rule for dynamic membership on security groups or on Microsoft 365 groups. If the device's association with a particular department changes in the future, it is automatically removed from the group. This feature requires an Azure AD Premium P1 license.


### Script group creation

You can also use Azure PowerShell to add a group using the New-AzureADGroup command as shown below.

```
New-AzureADGroup -Description "Marketing" -DisplayName "Marketing" -MailEnabled $false -SecurityEnabled $true -MailNickName "Marketing"

```

### Change membership for a group

Once a group is created, you can add or remove users (or groups) from it by editing the group membership by selecting the group and using the options under the Manage section.

![](https://github.com/amarnadh19/books/blob/main/images/az_ad_users_7.png?)