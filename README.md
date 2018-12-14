# hello-world

This will deploy a hello-world nodejs application as an AWS lambda function
accessible under an AWS API-gateway.


### Prerequisites

 - Terraform installed ( tested on version v0.11.10 )
 - AWS account
  
  
### Usage

The following directories are used:
```
├── nodejs
└── terraform
```
The code for the hello-world application is located in a subdirectory in the
nodejs directory.
The code to deploy the nodejs application is located in the terraform directory.
  
  
### Helper Script
  
There is a helper script - tf-aws-account-var - located in the terraform
directory - which will use the default profile found in ${HOME}/.aws/credentials
(if a profile is not specified it will use the default profile) to help set the
environment variables:

```bash
TF_VAR_aws_access_key_id
TF_VAR_aws_secret_access_key
```

To use a different AWS profile, use this script with specifying a different
profile, i.e.:

```bash
./tf-aws-account-var [profile_name]
```

This helper script does not need to be used (and likewise the script which it
creates to set the environment variable), as when the terraform code is
executed, it will prompt for both the `aws_access_key_id` and the
`aws_secret_access_key`.
  
  
### Deploying the web application.

```bash
cd terraform
terraform init
terraform plan
```

If everything looks okay:

```bash
terraform apply
```

Answer yes to the question, the url is provided as a terraform output called
`deployment_url`.  You are should be able to go to this address and you should
see 'Hello World'.


The nodejs code is deployed as a lamba function which is triggered via the AWS
API Gateway.

The `lamba.tf` terraform code creates a zip file of the nodejs code and uploads
it to AWS as a Lamba funtion. 

The `api_gateway.tf` sets up the API gateway to trigger the lamba function when
the endpoint is called. 
  
**Note: Please perform the following after the you have verified that everything
is working:**
```bash
terraform destroy
```
