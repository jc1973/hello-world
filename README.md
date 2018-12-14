# hello-world


### Prerequisites

 - Terraform installed ( tested on version v0.11.10 )
 - AWS account


### Usage


### Helper Script


There is a helperscript - tf-aws-account-var - in the terraform directory - 
this will use the default profile found in ${HOME}/.aws/credentials if a
profile is not specified, to help set the environment variables:

```bash
TF_VAR_aws_access_key_id
TF_VAR_aws_secret_access_key
```

if none are specified, if a different AWS profile is to be use please execute
this script as:

```bash
./tf-aws-account-var [profile_name]
```

You will 

terraform init
terraform plan
terraform apply
terraform destroy 
