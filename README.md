![Node.js CI](https://github.com/Devcognitio/hello-serverless/workflows/Node.js%20CI/badge.svg)
[![codecov](https://codecov.io/gh/Devcognitio/hello-serverless/branch/master/graph/badge.svg?token=4Z79Z3QLY3)](https://codecov.io/gh/Devcognitio/hello-serverless)

# hello-serverless
This is an example project where we show a complete example creating, testing and deploying an AWS Lambda using Serverless Framework, NodeJS, Jest, AWS-SDK, AWS-Mock, Codecov and github actions.

This Lambda exposes 2 endpoints through the AWS Api Gateway. The first gets an item from a DynamoDB table and the second one updates an item from the same table.
An example set of unit tests is provided and besides, the configuration to deploy the lambda locally and test it against a local DynamoDB instance.

## Commands:

````
  //Install all project dependencies
  >npm install
  
  //Start serverless offline mode
  >sls offline
  
  //Start local DynamoDB instance
  >sls dynamodb install
  >sls dynamodb start --migrate
````  

## CI/CD:

The following is the pipeline to run the whole CI/CD process (UnitTest, StaticAnalysis, Package and Deploy)

https://dev.azure.com/secheverris/Tests/_build?definitionId=12

The following are the commands to run each step:

UnitTest: 

````
npm run test:coverage
````

StaticAnalysis: 

````
npm run lint
````

Package and Deploy serverless: 

````
sls deploy
````
**Before to deploy the serverless, you have to set the AWS credentials, you can set it with the following command:
````
sls config credentials --provider aws --key <key> --secret <secret>
````
In this case, as we use Azure Devops, we use the Library to store the AWS ID, and the AWS Secret was stored hidden:

![Library](https://github.com/secheverri/hello-serverless/blob/master/images/Library.PNG).
