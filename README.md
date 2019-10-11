# AWS_CloudFormation
Various AWS CloudFormation Scripts that I have created.

I am creating this repo because I am having a very hard time finding CF Templates for some "edge case" templates that aren't as popular and used as much.

All of these templates will come in YAML and JSON format, feel free to use either. All of these templates are originally written in YAML and then I work to convert them to JSON, if there are issue with the JSON version, please let me know, but I have better exposure to YAML.

Please feel free to open issues for questions or issues that come up using these. I will work to fix them as time allows.

## Documentation
I will work to document these as well as I can, but please feel free to use these as needed. I will work to include a MarkDown file for each template that expands on some information needed to successfully use them.

# Note on Optional Items

If you are going to remove Optional items from the template, be sure you remove them everywhere (not just in Parameters).

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

This Maintnance Window runs the following Document: AWS-RunPatchBaseline

### Current Issues

* ~~Template error when using S3 Logging section #2~~ **Resolved**
