# AWS_CloudFormation
Various AWS CloudFormation Scripts that I have created.

I am creating this repo because I am having a very hard time finding CF Templates for some "edge case" templates that aren't as popular and used as much. I am also tired of looking on sites where peole state "Hey, I got my template working" and then refuse to share what they have put together.

I am hoping that this collection helps someone figure out how to do what they need to get done with CloudFormation.

All of these templates will come in YAML and JSON format, feel free to use either. All of these templates are originally written in YAML and then I work to convert them to JSON, if there are issue with the JSON version, please let me know, but I have better exposure to YAML.

Please feel free to open issues for questions, issues or requests that come up using these. I will work to fix/update them as time allows.

## Documentation
I will work to document these as well as I can, but please feel free to use these as needed. I will work to include a Wiki Page for each template that expands on some information needed to successfully use them.

The informaiton provided here is just to give you a quick glimpse into what the templates do, for details, please check out the Wiki pages for each of these templates.

# Note on Optional Items

If you are going to remove Optional items from the template, be sure you remove them **everywhere** (not just in Parameters).

# Validation Hints

For tempalte validation, I use cfn-lint (https://pypi.org/project/cfn-lint/) as well as CloudFormations Template Validator (using Design View). Also, **ALL** of these templates have been validated/tested and known to be wqorking in my environment. If you have issues, please open an issue and provide as much details as possible for me to help troubleshoot.

# Templates

## SSMAgent_cf.yaml
#### Validated and Tested
#### Wiki page created

This template was built to help automate (to a degree) the creation of a Systems Manager Maintenace Window and jobs to update the SSM Agents installed on variuos machines. This template should work in Windows and Linux distro's, but only tested on Windows. The Run Command Document used to build this schedule is an AWS Supplied Document that works with both platforms.

### Current Issues

* ~~SSMAgentcf.yaml - Failing on run #1~~ **Resolved**
* ~~Template error when using S3 Logging section #2~~ **Resolved**

## RunBaselineServerPatching_cf.yaml
#### Validated and Tested
#### Wiki page created

This document will cover the creation of a Windows/Linux Server Patching Maintenance Windows, Task and Targets for the maintenance.

This Maintnance Window runs the following Document: **AWS-RunPatchBaseline**

### Current Issues

* ~~Template error when using S3 Logging section #2~~ **Resolved**

## ElasticSearchService_*_cf.yaml
#### Validated and Tested
#### Wiki page created

**NOTE** In order to create Elastisearch Domain in AWS using CloudFormation verify you have the following Service Role created in IAM!!

AWSServiceRoleForAmazonElasticsearchService

If you do not have this Role, create it using the following CLi Command:

`aws iam create-service-linked-role --aws-service-name es.amazonaws.com`

### Current Issues

* No issues at this time

Multiple Templates here:

### ElasticSearchService_cf.yaml/json

* This tempaltes will use an existing VPC, but will create new Subnets and Security Group.

### ElasticSearchService_CreateSubNets_cf.yaml/json

* This tempaltes will use an existing VPC and Subnets, but will create new Security Group.

### ElasticSearchService_ExistingInfra_cf.yaml/json

* is template will use existing VPC, SubNets and SecurityGroup. No New Infra is built outside the Search Domain infra.
