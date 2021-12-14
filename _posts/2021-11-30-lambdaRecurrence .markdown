---
layout: post
title:  "How to schedule lambda functions to run automatically and repeatedly"
date:   2021-11-30 15:12:21 +0530
categories: Lambda Functions
---


We might run into a situation where it is necessary to run a lambda function on repeated basis, luckily we have cloudwatch for that on AWS to create a rule and achieve the same.How to do that?...We will see that below.

## We will create a simple lambda function
We can access lambda by searching for **Lambda** in the search  bar ,***Create a function*** we will name it _cronJobDemo_ ,we are creating a simple function in python language so the runtime would be python 3.9 next we would select **create a role with basic lambda permissions** this role would have access to cloudwatch logs and that would be enough for us as of now. If you have complicated job of accessing S3 bucket or dynamoDB you can go ahead and add those permissions accordingly.

Below is our simple lambda function in python:

![lambda](/assets/images/lambdaRecurrence/lambda code.png)

once the function is created we will set up cloudwatch .

## Rule Creation in CloudWatch
We can access cloudwatch by searching for **cloudwatch** in the search bar,In the left you would see **Events** tab below that **Rules** tab click on that

![cloudwatch](/assets/images/lambdaRecurrence/cloudwatch.png)

When you click on rules you might be prompted to select **Amazon EventBridge** ,we do not need eventBridge for our case so we can close that and continue with **Go to cloudwatch Events**

Click on Create Rule -> Select Schedule -> We will select 1 minute for our demo -> Add Target : Here the target is our lambda function , we will select our lambda function _cronJobDemo_ and click on configure details 


![ruleCreation](/assets/images/lambdaRecurrence/ruleCreation.png)

Name the rule and give it description ,in our example the rule is named _1minuteInvocation_ make sure it's enabled and create the rule.

BAM that's it!!! now you have a rule that triggers the lambda function every minute


![rule](/assets/images/lambdaRecurrence/rule.png)


Now you can verify if it's working by following the below steps:
* Open your lambda function 
* Select Monitor  in the tab 
* View logs in cloudwatch

You can check the logs and see our print statement getting logged every minute.

![logs](/assets/images/lambdaRecurrence/logs.png)

You can disable the rule from **clouwatch** if you want it to stop at any moment.


