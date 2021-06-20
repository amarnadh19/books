# AWS KMS (Key Management Services)

We get 20,000 KMS requests free of cost for free tier account per month.

AWS Key management services (KMS) is a managed service that makes it easy for you to create and control customer master keys (CMKs)

AWS KMS CMKs are protected by Hardware Security Modules (HSMs)

AWS KMS is intergrated with most other AWS services that encrypt your data.

AWS KMS is also integrate with AWS cloudTrail to log use of your CMKs for auditing regulatory and complainance needs.

You can create and manage your AWS KMS CMS keys.

You can use Kye management and cryptographic features directly in your application or through AWS services that are integrated with AWS KMS.

AWS KMS is integrated with AWS cloudTrail.

KMS is not supported in all regions.

## AWS KMS pricing

- Each key create in AWS KMS costs $1 per month until you delete it.

- API request access for key is also charged.

- AWS KMS provides a free tier of 20,000 requests per month.


## AWS KMS concepts

### Customer Master Keys

- Primary resources in AWS KMS

- A customer Master key is a logical representation of a master key.

- The CMK includes *metadata, keyid, description, creation date and keystate*

- It also contains key data to encrypt and decrypt data.

- AWS support Symmentic and ASymmentic CMKs

  - **Symmentic**: It represents 256 bit key that is used for encryption and decryption.

  - **ASymmentic**: It represents an RSA key pair that is used encryption and decryption or signin and verification or An ECC keypair that is used for signing and verification.

- To Manage KMS we can use 

  - AWS console

  - AWS SDK

  - AWS CLI

- AWS KMS supports three types of CMKs

  - Customer Managed CMKs

  - AWS Managed CMKs

  - AWS owned CMKs

#### Customer Managed CMKs

- you create own and manage keys.

- Customer managed keys can be used in cloudTrail and inCryptiographic operation.

- Customer managed CMKs incur a monthly fee or a fee to use in excess in free tier.


#### AWS Managed CMKs

- These are CMKs in your account that are created managed and used on your behalf by an AWS service that is integrated with AWS KMS.

- You can view managed CMKs but cannot rotate, change their key policies.

- We can identify them using below notation ``` aws/service-name```

- You do not pay a monthy fee for AWS managed CMKs.


#### AWS owned keys 

- There are collection of CMKs that are owned by a service and manage in multiple accounts.

- You do not need to create or manage these keys.

- You cannot view or audit them.

- You are not charged per month basis or usage fee or doesnot count to AWS Account quota.


### Data Keys

- These keys are used to encrypt data.

- You can use AWS KMS CMKs to generate, encrypt and decrypt data keys.

