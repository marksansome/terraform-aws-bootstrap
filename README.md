# terraform-aws-bootstrap

CloudFormation template to create a S3 bucket (with logging and policy) and DynamoDB table to store the state and lock information.

## Create Stack

    aws cloudformation create-stack --profile <aws_profile> --region ca-central-1 --stack-name bootstrap-terraform --template-body file://bootstrap-terraform.cf.yaml

## Example Terraform Example

Get the S3 bucket name and DynamoDB table name from the CloudFormation outputs.

    terraform {
        backend "s3" {
            bucket         = "tf-state-111222333444-ca-central-1"
            dynamodb_table = "tf-state-111222333444-ca-central-1"
            region         = "ca-central-1"
            encrypt        = true
        }
    }
