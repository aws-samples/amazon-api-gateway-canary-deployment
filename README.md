# Amazon API Gateway Canary Release Deployment
This stack creates an end to end implementation example to show how to do canary release deployment in Amazon API Gateway.


### Services Used
* <a href="https://aws.amazon.com/api-gateway/" target="_blank">Amazon API Gateway</a>
* <a href="https://aws.amazon.com/dynamodb/" target="_bank">Amazon DynamoDB</a>
* <a href="https://aws.amazon.com/iam/" target="_blank">AWS IAM</a>
* <a href="https://aws.amazon.com/cloudwatch/" target="_blank">Amazon CloudWatch</a>
* <a href="https://aws.amazon.com/s3/" target="_blank">Amazon S3</a>



### Requirements for deployment
* <a href="https://aws.amazon.com/cli/" target="_blank">AWS CLI</a>
* <a href="https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html" target="_blank">AWS SAM CLI v0.37.0+</a>


### Deploying

In the terminal, use the SAM CLI guided deployment the first time you deploy. Go to pre-stack folder
```bash
sam deploy -g
```

#### Choose options
You can choose the default for all options

```bash
## The name of the CloudFormation stack
Stack Name [sam-app]:

## The region you want to deploy in
AWS Region [us-east-1]:

## The name of the application (lowercase no spaces). This must be globally unique
Parameter AppName [canary-deployment]:

## Enables public client and local client for testing. (Less secure)
Parameter UseLocalClient [false]:

## Shows you resources changes to be deployed and requires a 'Y' to initiate deploy
Confirm changes before deploy [y/N]: 

## SAM needs permission to be able to create roles to connect to the resources in your template
Allow SAM CLI IAM role creation [Y/n]:

## Save your choice for later deployments
Save arguments to samconfig.toml [Y/n]:
```

SAM will then deploy the AWS CloudFormation stack to your AWS account and provide required outputs for the included client. This will create DynamoDB table , Rest API and an IAM role to access the DynamoDB table. 

After the first deploy you need to deploy the canary stack. Go to canary-stack folder and repeat the deployment using "sam deploy" same as above. Choose the default for all options


## Cleanup
1. Open the <a href="https://us-east-1.console.aws.amazon.com/cloudformation/home" target="_blank">CloudFormation console</a>
1. Locate a stack named *sam-app* 
1. Select the radio option next to it
1. Select **Delete**
1. Select **Delete stack** to confirm

*Note: If you opted to have access logs (on by default), you may have to delete the S3 bucket manually.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

