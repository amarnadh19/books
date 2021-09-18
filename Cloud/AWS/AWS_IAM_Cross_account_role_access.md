# IAM tutorial: Delegate access across AWS accounts using IAM roles

In this tutorial, imagine that the Production account is where live applications are managed. 

The Development account is a sandbox where developers and testers can freely test applications. 

In each account, application information is stored in Amazon S3 buckets. 

You manage IAM users in the Development account, where you have two IAM user groups: Developers and Testers. 

Users in both user groups have permissions to work in the Development account and access resources there. 

From time to time, a developer must update the live applications in the Production account. 

These applications are stored in an Amazon S3 bucket called productionapp.

![](https://github.com/amarnadh19/books/blob/main/images/AWS_IAM_Cross_Account_1.png?)

## Step1: Create a role

you create the role in the Production account and specify the Development account as a trusted entity. You also limit the role's permissions to only read and write access to the productionapp bucket

Anyone who is granted permission to use the role can read and write to the productionapp bucket.

### To obtain the development AWS account ID

- Sign in to the AWS Management Console as an administrator of the Development account, and open the IAM console at https://console.aws.amazon.com/iam/.

- Development account id 

### To create a role in the production account that can be used by the development account

- Sign in to the AWS Management Console as an administrator of the Production account, and open the IAM console.

- Before creating the role, prepare the managed policy that defines the permissions that the role requires. You attach this policy to the role in a later step.

- You want to set read and write access to the productionapp bucket. Although AWS provides some Amazon S3 managed policies, there isn't one that provides read and write access to a single Amazon S3 bucket. You can create your own policy instead.

- In the navigation pane on the left, choose Policies and then choose Create policy.

- Choose the JSON tab and copy the text from the following JSON policy document. Paste this text into the JSON text box, replacing the resource ARN (arn:aws:s3:::productionapp) with the real one appropriate to your S3 bucket.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListAllMyBuckets",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:ListBucket",
        "s3:GetBucketLocation"
       ],
      "Resource": "arn:aws:s3:::productionapp"
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject",
        "s3:DeleteObject"
      ],
      "Resource": "arn:aws:s3:::productionapp/*"
    }
  ]
}
```
- The ListBucket permission allows users to view objects in the productionapp bucket. The GetObject, PutObject, DeleteObject permissions allows users to view, update, and delete contents in the productionapp bucket.

- Resolve any security warnings, errors, or general warnings generated during policy validation, and then choose Review policy.

- On the Review page, type read-write-app-bucket for the policy name. Review the policy Summary to see the permissions granted by your policy, and then choose Create policy to save your work.

- The new policy appears in the list of managed policies.

- In the navigation pane on the left, choose Roles and then choose Create role.

- Choose the Another AWS account role type.

- For Account ID, type the Development account ID.

  This tutorial uses the example account ID 111111111111 for the Development account. You should use a valid account ID. If you use an invalid account ID, such as 111111111111, IAM does not let you create the new role.

- For now you do not need to require an external ID, or require users to have multi-factor authentication (MFA) in order to assume the role. So leave these options unselected. For more information, see Using multi-factor authentication (MFA) in AWS.

- Choose Next: Permissions to set the permissions that will be associated with the role.

-  Select the box next to the policy that you created previously.

- Then choose Next: Tags.

- Choose Next: Review and type UpdateApp for the role name.

- After reviewing the role, choose Create role.

- The UpdateApp role appears in the list of roles.

- Now you must obtain the role's Amazon Resource Name (ARN), which is a unique identifier for the role. When you modify the Developers and Testers user group's policy, you will specify the role's ARN to grant or deny permissions.

- To obtain the ARN for UpdateApp

- In the navigation pane of the IAM console, choose Roles.

- In the list of roles, choose the UpdateApp role.

- In the Summary section of the details pane, copy the Role ARN value.

- The Production account has an account ID of 999999999999, so the role ARN is arn:aws:iam::999999999999:role/UpdateApp. Ensure that you supply the real AWS account ID for your 'production' account.



## Step 2: Grant access to the role

At this point, both Testers and Developers user group members have permissions that allow them to freely test applications in the Development account. Here are the steps that are required to add permissions to allow switching to the role.

### To modify the Developers user group to allow them to switch to the UpdateApp role

- Sign in as an administrator in the Development account, and open the IAM console.

- Choose User groups, and then choose Developers.

- Choose the Permissions tab, choose Add permissions, and then choose Create inline policy.

- Choose the JSON tab.

  Add the following policy statement to allow the AssumeRole action on the UpdateApp role in the Production account. Be sure that you change PRODUCTION-ACCOUNT-ID in the Resource element to the actual AWS account ID of the Production account.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "sts:AssumeRole",
    "Resource": "arn:aws:iam::PRODUCTION-ACCOUNT-ID:role/UpdateApp"
  }
}
```
  The Allow effect explicitly allows the Developers group access to the UpdateApp role in the Production account. Any developer who tries to access the role will succeed.

- Choose Review policy.

- Type a Policy name like allow-assume-S3-role-in-production.

- Choose Create policy.

### To modify the testers user group to deny permission to assume the UpdateApp role

- Choose User groups, and then choose Testers.

- Choose the Permissions tab, choose Add permissions, and then choose Create inline policy.

- Choose the JSON tab.

  Add the following policy statement to deny the AssumeRole action on the UpdateApp role. Be sure that you change PRODUCTION-ACCOUNT-ID in the Resource element to the actual AWS account ID of the Production account.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Deny",
    "Action": "sts:AssumeRole",
    "Resource": "arn:aws:iam::PRODUCTION-ACCOUNT-ID:role/UpdateApp"
  }
}
```

  The Deny effect explicitly denies the Testers group access to the UpdateApp role in the Production account. Any tester who tries to access the role will get an access denied message.

- Choose Review policy.

- Type a Policy name like deny-assume-S3-role-in-production.

- Choose Create policy.


## Step 3: Switching role

### Switch roles (AWS CLI)

``` aws sts assume-role``` command and passes the role ARN to get temporary security credentials for that role. 

He then configures those credentials in environment variables so subsequent AWS CLI commands work using the role's permissions.

While David is using the role, he cannot use his power-user privileges in the Development account. The reason is that only one set of permissions can be in effect at a time.

```
aws sts assume-role --role-arn "arn:aws:iam::999999999999:role/UpdateApp" --role-session-name "David-ProdUpdate"
```

David can see below output

```
{
    "Credentials": {
        "SecretAccessKey": "wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY",
        "SessionToken": "AQoDYXdzEGcaEXAMPLE2gsYULo+Im5ZEXAMPLEeYjs1M2FUIgIJx9tQqNMBEXAMPLE
CvSRyh0FW7jEXAMPLEW+vE/7s1HRpXviG7b+qYf4nD00EXAMPLEmj4wxS04L/uZEXAMPLECihzFB5lTYLto9dyBgSDy
EXAMPLE9/g7QRUhZp4bqbEXAMPLENwGPyOj59pFA4lNKCIkVgkREXAMPLEjlzxQ7y52gekeVEXAMPLEDiB9ST3Uuysg
sKdEXAMPLE1TVastU1A0SKFEXAMPLEiywCC/Cs8EXAMPLEpZgOs+6hz4AP4KEXAMPLERbASP+4eZScEXAMPLEsnf87e
NhyDHq6ikBQ==",
        "Expiration": "2014-12-11T23:08:07Z",
        "AccessKeyId": "AKIAIOSFODNN7EXAMPLE"
    }
}

```
David sees the three pieces that he needs in the Credentials section of the output.

- AccessKeyId

- SecretAccessKey

- SessionToken

David needs to configure the AWS CLI environment to use these parameters in subsequent calls


To add the three values to the environment, David cuts and pastes the output of the previous step into the following commands.

```
set AWS_ACCESS_KEY_ID=AKIAIOSFODNN7EXAMPLE
set AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
set AWS_SESSION_TOKEN=AQoDYXdzEGcaEXAMPLE2gsYULo+Im5ZEXAMPLEeYjs1M2FUIgIJx9tQqNMBEXAMPLECvS
Ryh0FW7jEXAMPLEW+vE/7s1HRpXviG7b+qYf4nD00EXAMPLEmj4wxS04L/uZEXAMPLECihzFB5lTYLto9dyBgSDyEXA
MPLEKEY9/g7QRUhZp4bqbEXAMPLENwGPyOj59pFA4lNKCIkVgkREXAMPLEjlzxQ7y52gekeVEXAMPLEDiB9ST3UusKd
EXAMPLE1TVastU1A0SKFEXAMPLEiywCC/Cs8EXAMPLEpZgOs+6hz4AP4KEXAMPLERbASP+4eZScEXAMPLENhykxiHen
DHq6ikBQ==
```

Run the command to access the resources in the Production account.

```
aws s3 ls s3://productionapp
```