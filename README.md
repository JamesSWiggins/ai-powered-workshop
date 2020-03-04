# Welcome to Identify and mask health data in images or text - AIM353

### Welcome to this re:Invent workshop where you'll learn to use the [AI-Powered Health Data Masking Solution](https://aws.amazon.com/solutions/ai-powered-health-data-masking/) to mask PHI from within images and unstructured text.

## AWS Team

### First, a bit about us.

 |                            | Name                                 | Role                           |
 | -------------------------- | ------------------------------------ | ------------------------------ |
 | ![James](https://immersiondaylandingpage.s3.us-east-2.amazonaws.com/img/wiggjame.jpg) | James Wiggins (wiggjame@amazon.com)  | Solutions Architect Manager for Academic Medical Centers |
 | ![Aaron](https://immersiondaylandingpage.s3.us-east-2.amazonaws.com/img/ajfriedm.jpg) | Aaron Friedman (ajfriedm@amazon.com) | Principal Solutions Architect for Healthcare and Life Sciences   |


## Workshop Instructions

### 1. [AI-Powered Health Data Masking Deployment Guide](https://docs.aws.amazon.com/solutions/latest/ai-powered-health-data-masking/deployment.html)
### 2. Deploy the Stack, remember to provide a name and check the box at the end

![1](https://immersiondaylandingpage.s3.us-east-2.amazonaws.com/img/1.png)
![2](https://immersiondaylandingpage.s3.us-east-2.amazonaws.com/img/2.png)

### 3. Make sure you can see the CloudFormation outputs
    
![3](https://immersiondaylandingpage.s3.us-east-2.amazonaws.com/img/3.png)

### 4. [Make a new Permissions Policy](https://console.aws.amazon.com/iam/home#/policies$new?step=edit) to access the AI-Powered APIs.  Click the **JSON** tab and paste the below policy.  Replace **ACCOUNTID** with your AWS Account ID (no dashes), and **APIGATEWAYID** with the API Gateway ID from your CloudFormation output.
```
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Sid": "AIPowered",
                "Effect": "Allow",
                "Action": [
                    "apigateway:PUT",
                    "execute-api:Invoke",
                    "apigateway:POST",
                    "apigateway:GET"
                ],
                "Resource": [
                    "arn:aws:execute-api:us-east-1:ACCOUNTID:APIGATEWAYID/prod/*",
                    "arn:aws:apigateway:us-east-1::/restapis/APIGATEWAYID/resources/*"
                ]
            }
        ]
    }
```
### 5. [Create new Role for Sagemaker](https://console.aws.amazon.com/iam/home#/roles$new?step=type) using your Policy
### 6. Attach the permission policy you created to your new role
    
![4](https://immersiondaylandingpage.s3.us-east-2.amazonaws.com/img/4.png)

### 7. [Deploy a new SageMaker Notebook instance](https://console.aws.amazon.com/sagemaker/home?region=us-east-1#/notebook-instances/create)
### 8.  Provide your custom Role ARN during deployment
    
![5](https://immersiondaylandingpage.s3.us-east-2.amazonaws.com/img/5.png)

### 9. Download [this Jupyter Notebook](https://immersiondaylandingpage.s3.us-east-2.amazonaws.com/downloads/ai-powered-health-data-masking-demo.ipynb) and [this test image](https://immersiondaylandingpage.s3.us-east-2.amazonaws.com/downloads/sample.png) to your local computer.
### 10. Find the [S3 bucket](https://s3.console.aws.amazon.com/s3/home?region=us-east-1#) specified by the CloudFormation Output Key 'ImageBucketName'
    
![6](https://immersiondaylandingpage.s3.us-east-2.amazonaws.com/img/6.png)

### 11. Upload the test image (sample.png) into that S3 bucket
    
![7](https://immersiondaylandingpage.s3.us-east-2.amazonaws.com/img/7.png)

### 12. Open your [SageMaker Notebook Instance](https://console.aws.amazon.com/sagemaker/home?region=us-east-1#/notebook-instances), upload the test Jupyter Notebook (ai-powered-health-data-masking-demo.ipynb), and open it.
### 13. Read and run each cell in the notebook to understand how all of the APIs deployed as a part of this solution work.
### 14. This of some ways that you could use this solution in your organization or how it could be used by the industry in general.  We'll brainstorm for a little while once everyone has completed the lab!
