# Purpose

This document will cover the creation of an SSM Agent Update Maintenance Windows, Task and Targets for the maintenance.

*           Any items marked **(OPTIONAL)** can be removed if there is no need to specify this information

# Prerequisites

Thew following work will need to be completed to be able to use this template:

* EC2 Instances need to be Tagged
* The Key :: Value pair needs to be unique for this process. The below is a suggestion that can be used or another set can be created for this work.
* Suggested Key is: AgentUpdate
* Suggested Value: True
* Allowed Values: True or Fase
*           This is hard coded into the template and can be modified as needed - Just remove lines 46-48
*           AllowedValues:
            - True
            - False
* Run Command IAM Service Role ARN
* If you have not created a specific Role for this work, the default is:
*           arn:aws:iam::{AccountId}:role/aws-service-role/ssm.amazonaws.com/AWSServiceRoleForAmazonSSM
            Modify the {AccountID} to match your Account ID, you can find this in IAM in the upper left corner as soon as you enter the IAM Console (sample below)
* Finding your account ID (Console)

![Console AccountId](/images/account-id-iam-console.png)

* Finding your account ID (AWS CLi)
*           aws sts get-caller-identity
* ARN of the SNS Topic to send notifications through (Optional, can be removed if no notification is needed)
*           In order to get notifications (email, sms or other), you will need to create/use a topic, obtain the ARN and enter it here
* S3 Bucket Name to store logs / S3 Bucket prefix to assign logs for this job (Optional, can be removed if no notification is needed)
*           These need to already exist in order to be used

# Template Parameters
## Maintenance Window

* Maintenance Window Name (lowecase, no spaces)
* Maintenance Window Description (128 char max) **(OPTIONAL)**
* Timezone format as found here: https://docs.aws.amazon.com/redshift/latest/dg/time-zone-names.html
*           Use the labels on the linked page to ensure the job will run without issues in the timezone you select
            AWS will automatically convert this to UTC
* Maintenance Window Duration (in hours)
* Maintenance Window Cutoff (in hours before window closes) **(OPTIONAL)**
*           New jobs will not be initiated on instances once this time is reached. Be sure to allow for enough time for the job to run on all instances!
* Maintenance Window Schedule
*           Cron/Rate expression for schedule - Sample - cron(0 0 23 ? * WED *)
            This sample runs weekly, every Wed at 23:00 (11:00 pm)
* Documentation located here: https://docs.aws.amazon.com/lambda/latest/dg/tutorial-scheduled-events-schedule-expressions.html

## Maintenance Target Configuration

* Maintenance Target Config Name (lowercase, no spaces)
* Maintenance Target Config Description (128 char max) **(OPTIONAL)**
* Maintenance Target Tag Key (format: tag:{keyName})
*           Value should look like: tag:AgentUpdate
* Maintenance Target Key Value
*           For this template, the only value is True or False
            Case Sensitive

## Maintenance Run Command Configuration

* Run Command Name (lowercase, no spaces)
* Run Command Task Priority
*           Values 0 - 5
            Default set to 1 - This does not need to be changed
* Run Command Max Concurrency **(OPTIONAL)**
*           You can use an Integer or a Percent
* Run Command Max Error Rate **(OPTIONAL)**
*           You can use an Integer or a Percent
* ARN of the SNS Topic to send notifications through **(OPTIONAL)**
*           Must be a VALID ARN
* S3 Bucket Name to store logs **(OPTIONAL)**
*           Bucket Name, NOT ARN
* S3 Bucket prefix to assign logs for this job **(OPTIONAL)**
