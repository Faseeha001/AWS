# AWS Command Line Interface (CLI) Guide

## Introduction
This README provides an overview and basic usage of the AWS Command Line Interface (CLI). The AWS CLI allows you to interact with various AWS services directly from the command line.

## Prerequisites
Before using the AWS CLI, ensure you have the following:
- AWS account
- AWS CLI installed (installation instructions: [AWS CLI Installation Guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html))
- AWS credentials configured (configuration instructions: [AWS CLI Configuration Guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html))

## Usage
To use the AWS CLI, open your terminal and type `aws` followed by the desired command and its options. Here are some common commands:

### Basic Commands
1. **aws configure**: Configures AWS credentials.
  <img width="532" alt="image" src="https://github.com/Faseeha001/Terraform/assets/169563689/86b4bb92-814e-4499-a775-bad299ab200a">
  
2. **`aws version**`: Displays the AWS CLI version.
   <img width="531" alt="image" src="https://github.com/Faseeha001/AWS/assets/169563689/81e9ce7a-246e-4808-ac6c-eaedb602e05a">

### S3 Commands
1.`**aws s3 ls**`: Lists buckets or objects in a bucket.
2.`aws s3 cp <localPath> <s3Path>`: Copies a file or directory to/from Amazon S3.
3. `aws s3 sync <localPath> <s3Path>`: Syncs files and directories to/from Amazon S3.

### EC2 Commands
- `aws ec2 describe-instances`: Describes EC2 instances.
- `aws ec2 start-instances --instance-ids <instance-id>`: Starts an EC2 instance.
- `aws ec2 stop-instances --instance-ids <instance-id>`: Stops an EC2 instance.

### IAM Commands
- `aws iam list-users`: Lists IAM users.
- `aws iam create-user --user-name <username>`: Creates a new IAM user.
- `aws iam delete-user --user-name <username>`: Deletes an IAM user.

### Lambda Commands
- `aws lambda list-functions`: Lists Lambda functions.
- `aws lambda create-function --function-name <function-name> --runtime <runtime> --handler <handler> --role <role-arn> --code <code>`: Creates a new Lambda function.
- `aws lambda delete-function --function-name <function-name>`: Deletes a Lambda function.

## Additional Resources
For more information on AWS CLI commands and options, refer to the [AWS CLI Documentation](https://docs.aws.amazon.com/cli/latest/reference/index.html).

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.