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


There is a helperscript - tf-aws-account-var - in the terraform directory - this
will use the default profile found in ${HOME}/.aws/credentials if a profile is
not specified, to help set the environment variables:

```bash
TF_VAR_aws_access_key_id
TF_VAR_aws_secret_access_key
```

If an AWS profile is not specified. To use a different AWS profile, use this
script with specifying a different profile:

```bash
./tf-aws-account-var [profile_name]
```

You will 

terraform init
terraform plan
terraform apply
terraform destroy 
