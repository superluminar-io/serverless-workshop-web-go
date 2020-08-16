---
title: Lab 5 - Safe Deployment
weight: 35
---

**In this Lab we will**:

- Implement safe deployments using AWS SAM
- Learn about Lambda versions and aliases
- Learn about different deployment types (linear vs. canary)
- Use Cloudwatch Alarms to check if a change is safe to deploy to production

**You completed this lab if you**:

- Have implemented [SAM Safe Deployment](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/automating-updates-to-serverless-apps.html) for at least one function
- Watched a deployment in the [Code Deploy Console](https://eu-central-1.console.aws.amazon.com/codesuite/codedeploy/deployments?region=eu-central-1)

**Why is this important?**

Even the best CI/CD systems and integration test suites can not catch all errors. Therefore, it is necessary to have
a (automated!) way of testing your changes and rolling back to a sane version while you release them to your customers.

AWS SAM offers a great way of releasing your changes gradually to your customers and reverting as soon as an error occurs. 

## Safe Deployments with AWS SAM

Blue/Green deployments is a [feature of AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html#welcome-deployment-overview-blue-green). 
Thanks to the implementation in SAM it is easy to make use of in our project.

Steps to take in this lab:

- Activate aliases for the function you want to use safe deployments for (see: `AutoPublishAlias`)
- Configure a `DeploymentPreference` for this function and 
- Decide which [deployment type](https://github.com/awslabs/serverless-application-model/blob/master/docs/safe_lambda_deployments.rst#traffic-shifting-configurations) to use
- Create and configure one or more Cloudwatch Alarms
- Optionally: Create and configure `PreTraffic` and `PostTraffic` [hooks](https://awslabs.github.io/serverless-application-model/safe_lambda_deployments.html#pretraffic-posttraffic-hooks)

## Hints

- [Traffic shifting using CodeDeploy](https://github.com/awslabs/serverless-application-model/blob/master/docs/safe_lambda_deployments.rst#traffic-shifting-using-codedeploy)
- You can find an example implementation here: https://github.com/superluminar-io/serverless-workshop-go/compare/lab4..lab5?expand=1
