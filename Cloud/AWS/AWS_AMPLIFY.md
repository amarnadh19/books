https://docs.amplify.aws/cli/teams/overview

https://aws.amazon.com/blogs/mobile/configure-environment-variables-and-secrets-for-your-lambda-functions-with-amplify-cli/


# Configure-environment-variables-and-secrets-for-your-lambda-functions-with-amplify-cli/


# AWS Amplify
## Step 1: Install amplify cli
## Step 2: Amplify configure
## Step 3: Amplify init 

```
const aws = require('aws-sdk');
const REGION = process.env.REGION
var client = new aws.SecretsManager({
    region: REGION // Your region
});
var secretName = process.env.SECRET_NAME 
exports.handler = async (event) => {
    // TODO implement
    const { Parameters } = await (new aws.SSM())
      .getParameters({ 
        Names: ["SECRET_TOKEN"].map(secretName => process.env[secretName]),
        WithDecryption: true,
      })
      .promise();
      let secretVal = await client.getSecretValue({ SecretId: secretName }).promise();
      let SECRETVALUE = secretVal["SecretString"]; 
    const SERVICE_URL = process.env.SERVICE_URL;
    const SECRET_TOKEN = Parameters.pop().Value;
    const response = {

        statusCode: 200,
    //  Uncomment below to enable CORS requests
    //  headers: {
    //      "Access-Control-Allow-Origin": "*",
    //      "Access-Control-Allow-Headers": "*"
    //  }, 
        //body: JSON.stringify('Hello from Lambda!'),
        body: `SERVICE_URL: ${SERVICE_URL}, SECRET_TOKEN: ${SECRET_TOKEN}, val: ${SECRETVALUE}`
        
    };
    return response;
};

```
## IAM ROlE which was assigned to Lambda function

### amplify-function-secrets-policy:

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "ssm:GetParameter",
                "ssm:GetParameters"
            ],
            "Resource": "arn:aws:ssm:us-east-1:457846499801:parameter/amplify/d1kbbw4ezpc6gf/dev/AMPLIFY_reactamplifiede081c08a_*",
            "Effect": "Allow"
        }
    ]
}

### lambda execution policy:

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "logs:CreateLogGroup",
                "logs:CreateLogStream",
                "logs:PutLogEvents"
            ],
            "Resource": "arn:aws:logs:us-east-1:457846499801:log-group:/aws/lambda/reactamplifiede081c08a-dev:log-stream:*",
            "Effect": "Allow"
        }
    ]
}

### SecretsManagerReadWrite policy which can add directly


