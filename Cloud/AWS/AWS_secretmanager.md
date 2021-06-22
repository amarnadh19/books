# Secret Manager

## What Is AWS Secrets Manager?

Secrets Manager enables you to replace hardcoded credentials in your code, including passwords, with an API call to Secrets Manager to retrieve the secret programmatically. 

Also, you can configure Secrets Manager to automatically rotate the secret for you according to a specified schedule. 


## Getting started with Secrets Manager

- **Secrets Manager administrator** – Administers the Secrets Manager service. Grants permissions to individuals who can then perform the other roles listed here.

- **Database or service administrator** – Administers the database or service with secrets stored in Secrets Manager. Determines and configures the rotation and expiration settings for their secrets.

- **Application developer** – Creates the application, and then configures the application to request the appropriate credentials from Secrets Manager.


## Key terms and concepts for AWS Secrets Manager

### Secret

In Secrets Manager, a secret consists of a set of credentials, user name and password, and the connection details used to access a secured service.

Secrets Manager uses IAM permission policies to ensure only authorized users can access or modify the secret. 

Secrets Manager provides this flexibility by storing the secret as key-value pairs of text strings.

