------------------------------------------------------------------------------
# Create the EC2 instance in the specified VPC & Subnet
# VPC & Subnet => MUST be already setup - available via Cross Stack Reference
# Parameters:
#   - key-pair-name
#   - NetworkStack Default = TestVPC
#   - Subnet  Default = SnA1
#   - Security group    Default = SG-Bastion
#   - Role to be added to the EC2     - Managed policy = Administrator
# 
# Creates a Security Group - update as needed
------------------------------------------------------------------------------

Make changes to the parameters.json to set the parameters

- Creation
# This would require all params to be specified - rather use the JSON file
aws cloudformation create-stack --stack-name TestEc2 --template-body file://ec2/ec2-single-instance.yaml --parameters ParameterKey=KeyNameParameter,ParameterValue=raj-key-pair

aws cloudformation create-stack --stack-name TestEc2 --template-body file://ec2/ec2-single-instance.yaml --parameters file://ec2/parameters.json --capabilities CAPABILITY_IAM 

- Update
aws cloudformation update-stack --stack-name TestEc2 --template-body file://ec2/ec2-single-instance.yaml --parameters ParameterKey=KeyNameParameter,ParameterValue=raj-key-pair --capabilities CAPABILITY_IAM 

aws cloudformation update-stack --stack-name TestEc2 --template-body file://ec2/ec2-single-instance.yaml --parameters file://ec2/parameters.json --capabilities CAPABILITY_IAM 

- Delete
aws cloudformation delete-stack --stack-name TestEc2 