

# AWS CLI Commands Cheat Sheet

This README provides a handy reference for common AWS CLI commands. The AWS Command Line Interface (CLI) allows you to interact with various AWS services from the command line. Make sure you have the AWS CLI installed and configured before using these commands.

## Table of Contents

1. [Installation](#installation)
2. [Configuration](#configuration)
3. [Basic Commands](#basic-commands)
4. [S3 Commands](#s3-commands)
5. [EC2 Commands](#ec2-commands)
6. [Lambda Commands](#lambda-commands)
7. [DynamoDB Commands](#dynamodb-commands)
8. [IAM Commands](#iam-commands)
9. [CloudFormation Commands](#cloudformation-commands)

## Installation

You can install the AWS CLI by following the instructions in the [official AWS documentation](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html).

## Configuration

Before using the AWS CLI, configure your credentials using the `aws configure` command:



```bash
aws configure
```

Follow the prompts to enter your AWS Access Key ID, Secret Access Key, default region, and output format.

## Basic Commands

- Get AWS CLI version:
  ```bash
  aws --version
  ```

- List available AWS regions:
  ```bash
  aws ec2 describe-regions
  ```
## EKS Commands

- connecting the eks cluster to the machine :
  ```bash
  aws eks --region <eg: us-west-1> update-kubeconfig --name <cluster-name>
  ```
  
  cluster status :
  ```bash
  aws eks --region <eg:us-west-1> describe-cluster --name <cluster-name> --query cluster.status
  ```
## S3 Commands

- List buckets:
  ```bash
  aws s3 ls
  ```

- Create a new S3 bucket:
  ```bash
  aws s3 mb s3://my-bucket-name
  ```

- Upload a file to S3:
  ```bash
  aws s3 cp my-file.txt s3://my-bucket-name/
  ```

- Download a file from S3:
  ```bash
  aws s3 cp s3://my-bucket-name/my-file.txt .
  ```

## EC2 Commands

- List EC2 instances:
  ```bash
  aws ec2 describe-instances
  ```

- Start an EC2 instance:
  ```bash
  aws ec2 start-instances --instance-ids i-1234567890abcdef0
  ```

- Stop an EC2 instance:
  ```bash
  aws ec2 stop-instances --instance-ids i-1234567890abcdef0
  ```

## Lambda Commands

- List Lambda functions:
  ```bash
  aws lambda list-functions
  ```

- Invoke a Lambda function:
  ```bash
  aws lambda invoke --function-name my-function output.txt
  ```

## DynamoDB Commands

- List DynamoDB tables:
  ```bash
  aws dynamodb list-tables
  ```

- Create a DynamoDB table:
  ```bash
  aws dynamodb create-table --table-name my-table ...
  ```

- Query a DynamoDB table:
  ```bash
  aws dynamodb query --table-name my-table ...
  ```

## IAM Commands

- List IAM users:
  ```bash
  aws iam list-users
  ```

- Create an IAM user:
  ```bash
  aws iam create-user --user-name my-user
  ```

- Attach an IAM policy to a user:
  ```bash
  aws iam attach-user-policy --user-name my-user --policy-arn arn:aws:iam::aws:policy/AmazonS3FullAccess
  ```

## CloudFormation Commands

- Create a CloudFormation stack:
  ```bash
  aws cloudformation create-stack --stack-name my-stack ...
  ```

- Describe a CloudFormation stack:
  ```bash
  aws cloudformation describe-stacks --stack-name my-stack
  ```

This README provides a quick reference to some common AWS CLI commands. For more details and additional commands, refer to the [AWS CLI documentation](https://docs.aws.amazon.com/cli/latest/index.html).









