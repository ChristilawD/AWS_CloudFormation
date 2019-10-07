# AWS_CloudFormation
Various AWS CloudFormation Scripts that I have created.

I am crewating this repor because I am having a very hard time finding CF Templates for some "edge case" templates that aren't as popular and used as much.

All of these templates will come in YAML format, feel free to convert as needed.

AWS Supplied Documents are used for all of these jobs. Notes will be added if/when custom documents are used (and they will be supplied).

Please feel free to open issues for questions or issues that come up using these.

## Documentation
I will work to document these as well as I can, but please feel free to use these as needed.

# Templates

## SSMAgent_cf.yaml

This template was built to help automate (to a degree) the creation of a Systems Manager maintenace window and jobs to update the SSM agent installed on variuos machines. This template should work in Windows and Linux distro's, but only tested on Windows. The Dpocument used to build this schedule is an AWS Supplied Document that work with both platforms.

### Current Issues

SSMAgentcf.yaml - Failing on run #1
