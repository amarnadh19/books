# Azure Directory 

## Create a new directory

An organization (tenant) has one associated default Azure AD directory. However, owners can create additional directories to support the development or testing purposes or because they want to have separate directories to synchronize with their local Windows Server AD forests.

1) Sign in to the Azure portal.

2) On the Azure home page, under Azure services, select Create a resource. The Create a resource pane appears.

3) In the left menu pane, select Identity, and then search for an select Azure Active Directory. The Azure Active Directory pane appears.

4) Select Create. The Create tenant pane appears.

5) Enter the following values for each setting.

   - **Organization name:** Enter a name for the directory to help distinguish it from your other directories. The directory to be created will be used in production; provide a name that your users will recognize as your organization's name. You can change the name later if you want.

   - **Initial domain name:** Enter a domain name associated with your organization. Azure will give a validation error unless the domain is not known. The default domain name will always have the suffix .onmicrosoft.com. You can not change the default domain. If you choose to, you can add a custom domain owned by your organization so defined users can use a traditional company email such as john@contoso.com.

   - **Country or region:** Select the country the directory should reside. The country will identify the region and data center where the Azure AD instance will live; you can not change it later.

![](https://github.com/amarnadh19/books/blob/main/images/az_ad_directory_1.png?)

6) Select Create to create the new directory. A free tier directory will be created where you can add users, create roles, register apps and devices, and control licenses.

After you have created the directory, select Click here to manage your new tenant to go to the Overview dashboard that lets you control all directory aspects.

![](https://github.com/amarnadh19/books/blob/main/images/az_ad_directory_2.png?)

