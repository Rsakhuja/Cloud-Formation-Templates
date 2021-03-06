---------------------------------------------------------------------
# VPC With 1 Private Subnet with NAT
---------------------------------------------------------------------

T.B.D.

---------------------------------------------------------------------
# VPC With 3 Subnets
# This template creates a Test VPC with 3 Subnets as explained below
---------------------------------------------------------------------

1. CIDR Block = 10.10.0.0/16

# Subnet A  AZ A => Subnet => 
- VpcTestSnA1  10.10.0.0/20       Public
- VpcTestSnA2  10.10.16.0/20

# Subnet B  AZ B => Subnet => 
- VpcTestSnB1  10.10.32.0/20      Public
- VpcTestSnB2  10.10.48.0/20

# Subnet C  AZ C => Subnet => 
- VpcTestSnC1  10.10.64.0/20      Public
- VpcTestSnC2  10.10.128.0/20

2. Create an IGW
3. Create a RouteTable with Public Default Route to IGW
4. Associate the RuteTable to Subnet A1, B1, C1
5. Creates Security Groups for Bastian/Internal resources


## Using the Template ##
========================
Creates a VPC with the configuration described above

From Console
============
- Open Console
- Go to Cloudfront
- Upload the vpc-test.yaml template
- Give a name to the stack "vpctest"

From Terminal
=============
- cd to the vpc folder

- Creation
aws cloudformation create-stack --stack-name TestVPC --template-body file://./vpc-3-subnet-setup.yaml 

- Update 
aws cloudformation update-stack --stack-name TestVPC --template-body file://vpc/vpc-3-subnet-setup.yaml 

- Delete
aws cloudformation delete-stack --stack-name Test-VPC