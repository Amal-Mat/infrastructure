# VPC and networking resources using CloudFormation Template

1. Create a Virtual Private Cloud (VPC)
2. Create an Internet Gateway
3. Attach the internet gateway to VPC
4. Create a Route Table
5. Create 3 subnets with each in different availability zones
6. Attach all 3 subnets to Route Table
7. Create a route with destination CIDR block of 0.0.0.0/0 and connect it to internet gateway.

# AWS CLI Setup

1. Install AWS CLI
2. Create two profiles (dev and demo) using aws configure command and enter the credentials.
3. Verify if there are 2 profiles in AWS CLI - aws configure list-profiles

# Creating of VPC

Parameters to be included - Stack Name, VPC Name, AWS Region, VpcCIDR, Subnet1CIDR, Subnet2CIDR, Subnet3CIDR

CLI Command -
aws cloudformation --profile dev create-stack --stack-name testStack1 --template-body file://csye6225-infra.yml --region us-east-1 --parameters ParameterKey=VpcName,ParameterValue=testVPC ParameterKey=VpcCIDR,ParameterValue=100.100.0.0/16 ParameterKey=Subnet1CIDR,ParameterValue=100.100.1.0/24 ParameterKey=Subnet2CIDR,ParameterValue=100.100.2.0/24 ParameterKey=Subnet3CIDR,ParameterValue=100.100.3.0/24

# Deleting a VPC

Parameters to be included - Stack Name, AWS Region

CLI Command -
aws cloudformation --profile dev delete-stack --stack-name testStack1 --region us-east-1

