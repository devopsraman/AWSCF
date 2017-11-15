
## Description

Build an AWS User Jumpbox for RDP access.

#### Metadata

 * **AWS::CloudFormation::Interface**: {u'ParameterGroups': [{u'Parameters': [u'VPCID', u'EC2Subnets'], u'Label': {u'default': u'VPC Settings'}}, {u'Parameters': [u'ImageId', u'InstanceType'], u'Label': {u'default': u'Device Settings'}}]}
 * **LastUpdated**: 2016-06-23
 * **UpdatedBy**: RSabounds (Alan Bounds) & bran8120 (Brandon Cleary)

## Parameters

 * **BastionType** - EC2 instance type.
  * Default: `Rackspace`
 * **EC2Subnets** - Subnet where the instance will be deployed
 * **EnableClientSecurityGroup** - Enables CloudFormation to create a security group you can add instances to that can be accessed by the Jumpbox. Should be false if creating this Jumpbox for racker use only.
  * Default: `False`
 * **Environment** - Application environment for which this network is being created. e.g. Development/Production.
  * Default: `Development`
 * **InstanceType** - EC2 instance type.
  * Default: `t2.small`
 * **StageOrBuild** - Stage or Build Bastion?
  * Default: `Build`
 * **TargetSecurityGroupId** - Id of the Security Group containing the EC2 instance you want access to.
 * **VPCID** - VPC to deploy EC2 instance.

## Conditions

 * **BuildStatus** - `{u'Fn::Equals': [{u'Ref': u'StageOrBuild'}, u'Build']}`
 * **CreateClientSG** - `{u'Fn::Equals': [{u'Ref': u'EnableClientSecurityGroup'}, u'True']}`
 * **ModifyTargetSG** - `{u'Fn::And': [{u'Fn::Equals': [{u'Ref': u'EnableClientSecurityGroup'}, u'False']}, {u'Fn::Equals': [{u'Ref': u'StageOrBuild'}, u'Build']}]}`

## Mappings

 * **AWSRegionArch2AMI**:
  * `(u'us-east-1', {u'64': u'ami-79dc1b14'})`
  * `(u'ap-northeast-1', {u'64': u'ami-447a9d25'})`
  * `(u'eu-west-1', {u'64': u'ami-29eb7e5a'})`
  * `(u'ap-northeast-2', {u'64': u'ami-3e75bd50'})`
  * `(u'ap-southeast-1', {u'64': u'ami-5bf72138'})`
  * `(u'ap-southeast-2', {u'64': u'ami-4c6d422f'})`
  * `(u'us-west-2', {u'64': u'ami-8db945ed'})`
  * `(u'us-west-1', {u'64': u'ami-b8c5bcd8'})`
  * `(u'eu-central-1', {u'64': u'ami-827d90ed'})`
  * `(u'sa-east-1', {u'64': u'ami-588f0734'})`
 * **JumpBox**:
  * `(u'Customer', {u'EC2IAMPolicyStatement': [{u'Action': [u'ssm:DescribeAssociation', u'ssm:CreateAssociation', u'ssm:GetDocument', u'ssm:ListAssociations', u'ssm:UpdateAssociationStatus', u'ssm:UpdateInstanceInformation'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u'ec2messages:AcknowledgeMessage', u'ec2messages:DeleteMessage', u'ec2messages:FailMessage', u'ec2messages:GetEndpoint', u'ec2messages:GetMessages', u'ec2messages:SendReply'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u'cloudwatch:PutMetricData'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u'route53:*'], u'Resource': [u'*'], u'Effect': u'Allow'}, {u'Action': [u'ec2:DescribeInstanceStatus', u'ec2:DescribeInstances', u'autoscaling:DescribeAutoScalingGroups', u'autoscaling:DescribeAutoScalingInstances'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u'ds:CreateComputer', u'ds:DescribeDirectories'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u'logs:CreateLogGroup', u'logs:CreateLogStream', u'logs:DescribeLogGroups', u'logs:DescribeLogStreams', u'logs:PutLogEvents'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u's3:PutObject', u's3:GetObject', u's3:AbortMultipartUpload', u's3:ListMultipartUploadParts', u's3:ListBucketMultipartUploads'], u'Resource': u'*', u'Effect': u'Allow'}], u'ScalingCreateTimeOut': u'30M', u'WaitOnResourceSignals': u'True', u'ScalingUpdateTimeOut': u'30M', u'JumpBoxSecurityGroupIngress': [{u'ToPort': u'443', u'IpProtocol': u'tcp', u'CidrIp': u'0.0.0.0/0', u'FromPort': u'443'}], u'ServerGroupName': u'JumpBox', u'update': [u'cfnConfig', u'finalize'], u'RootVolumeSize': u'40', u'RootVolumeType': u'gp2', u'ScalingTermination': u'1', u'init': [u'cfnConfig', u'finalize'], u'ScalingMin': u'1', u'ScalingMax': u'1', u'RootVolumeDeleteOnTermination': u'True', u'InstancePublicIP': u'True'})`
  * `(u'Rackspace', {u'EC2IAMPolicyStatement': [{u'Action': [u'ssm:DescribeAssociation', u'ssm:CreateAssociation', u'ssm:GetDocument', u'ssm:ListAssociations', u'ssm:UpdateAssociationStatus', u'ssm:UpdateInstanceInformation'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u'ec2messages:AcknowledgeMessage', u'ec2messages:DeleteMessage', u'ec2messages:FailMessage', u'ec2messages:GetEndpoint', u'ec2messages:GetMessages', u'ec2messages:SendReply'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u'cloudwatch:PutMetricData'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u'route53:*'], u'Resource': [u'*'], u'Effect': u'Allow'}, {u'Action': [u'ec2:DescribeInstanceStatus', u'ec2:DescribeInstances', u'autoscaling:DescribeAutoScalingGroups', u'autoscaling:DescribeAutoScalingInstances'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u'ds:CreateComputer', u'ds:DescribeDirectories'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u'logs:CreateLogGroup', u'logs:CreateLogStream', u'logs:DescribeLogGroups', u'logs:DescribeLogStreams', u'logs:PutLogEvents'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u's3:PutObject', u's3:GetObject', u's3:AbortMultipartUpload', u's3:ListMultipartUploadParts', u's3:ListBucketMultipartUploads'], u'Resource': u'*', u'Effect': u'Allow'}], u'ScalingCreateTimeOut': u'30M', u'WaitOnResourceSignals': u'True', u'ScalingUpdateTimeOut': u'30M', u'JumpBoxSecurityGroupIngress': [{u'ToPort': u'3389', u'IpProtocol': u'tcp', u'CidrIp': u'172.99.99.10/32', u'FromPort': u'3389'}, {u'ToPort': u'3389', u'IpProtocol': u'tcp', u'CidrIp': u'134.213.179.10/32', u'FromPort': u'3389'}, {u'ToPort': u'3389', u'IpProtocol': u'tcp', u'CidrIp': u'161.47.0.10/32', u'FromPort': u'3389'}, {u'ToPort': u'3389', u'IpProtocol': u'tcp', u'CidrIp': u'146.20.2.10/32', u'FromPort': u'3389'}, {u'ToPort': u'3389', u'IpProtocol': u'tcp', u'CidrIp': u'134.213.178.10/32', u'FromPort': u'3389'}, {u'ToPort': u'3389', u'IpProtocol': u'tcp', u'CidrIp': u'119.9.122.10/32', u'FromPort': u'3389'}, {u'ToPort': u'3389', u'IpProtocol': u'tcp', u'CidrIp': u'119.9.148.10/32', u'FromPort': u'3389'}, {u'ToPort': u'3389', u'IpProtocol': u'tcp', u'CidrIp': u'72.3.128.84/32', u'FromPort': u'3389'}, {u'ToPort': u'3389', u'IpProtocol': u'tcp', u'CidrIp': u'69.20.0.1/32', u'FromPort': u'3389'}, {u'ToPort': u'3389', u'IpProtocol': u'tcp', u'CidrIp': u'50.57.22.125/32', u'FromPort': u'3389'}, {u'ToPort': u'3389', u'IpProtocol': u'tcp', u'CidrIp': u'120.136.34.22/32', u'FromPort': u'3389'}, {u'ToPort': u'3389', u'IpProtocol': u'tcp', u'CidrIp': u'212.100.225.49/32', u'FromPort': u'3389'}, {u'ToPort': u'3389', u'IpProtocol': u'tcp', u'CidrIp': u'212.100.225.42/32', u'FromPort': u'3389'}, {u'ToPort': u'3389', u'IpProtocol': u'tcp', u'CidrIp': u'119.9.4.2/32', u'FromPort': u'3389'}, {u'ToPort': u'443', u'IpProtocol': u'tcp', u'CidrIp': u'0.0.0.0/0', u'FromPort': u'443'}], u'ServerGroupName': u'JumpBox', u'update': [u'cfnConfig', u'finalize'], u'RootVolumeSize': u'40', u'RootVolumeType': u'gp2', u'ScalingTermination': u'1', u'init': [u'cfnConfig', u'finalize'], u'ScalingMin': u'1', u'ScalingMax': u'1', u'RootVolumeDeleteOnTermination': u'True', u'InstancePublicIP': u'True'})`
  * `(u'Custom', {u'EC2IAMPolicyStatement': [{u'Action': [u'ssm:DescribeAssociation', u'ssm:CreateAssociation', u'ssm:GetDocument', u'ssm:ListAssociations', u'ssm:UpdateAssociationStatus', u'ssm:UpdateInstanceInformation'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u'ec2messages:AcknowledgeMessage', u'ec2messages:DeleteMessage', u'ec2messages:FailMessage', u'ec2messages:GetEndpoint', u'ec2messages:GetMessages', u'ec2messages:SendReply'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u'cloudwatch:PutMetricData'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u'route53:*'], u'Resource': [u'*'], u'Effect': u'Allow'}, {u'Action': [u'ec2:DescribeInstanceStatus', u'ec2:DescribeInstances', u'autoscaling:DescribeAutoScalingGroups', u'autoscaling:DescribeAutoScalingInstances'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u'ds:CreateComputer', u'ds:DescribeDirectories'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u'logs:CreateLogGroup', u'logs:CreateLogStream', u'logs:DescribeLogGroups', u'logs:DescribeLogStreams', u'logs:PutLogEvents'], u'Resource': u'*', u'Effect': u'Allow'}, {u'Action': [u's3:PutObject', u's3:GetObject', u's3:AbortMultipartUpload', u's3:ListMultipartUploadParts', u's3:ListBucketMultipartUploads'], u'Resource': u'*', u'Effect': u'Allow'}], u'ScalingCreateTimeOut': u'30M', u'WaitOnResourceSignals': u'True', u'ScalingUpdateTimeOut': u'30M', u'JumpBoxSecurityGroupIngress': [{u'ToPort': u'443', u'IpProtocol': u'tcp', u'CidrIp': u'0.0.0.0/0', u'FromPort': u'443'}], u'ServerGroupName': u'JumpBox', u'update': [u'cfnConfig', u'finalize'], u'RootVolumeSize': u'40', u'RootVolumeType': u'gp2', u'ScalingTermination': u'1', u'init': [u'cfnConfig', u'finalize'], u'ScalingMin': u'1', u'ScalingMax': u'1', u'RootVolumeDeleteOnTermination': u'True', u'InstancePublicIP': u'True'})`

## Resources

 * **BastionServer** - `AWS::EC2::Instance`
 * **ClientSecurityGroup** - `AWS::EC2::SecurityGroup`
 * **InstanceRole** - `AWS::IAM::Role`
 * **InstanceRoleInstanceProfile** - `AWS::IAM::InstanceProfile`
 * **InstanceRolePolicies** - `AWS::IAM::Policy`
 * **JumpboxSecurityGroup** - `AWS::EC2::SecurityGroup`
 * **ModifyTargetSecurityGroup** - `AWS::EC2::SecurityGroupIngress`
 * **SSMSetUser** - `AWS::SSM::Document`

## Outputs

 * **AZ** - `{u'Fn::GetAtt': [u'BastionServer', u'AvailabilityZone']}`
 * **ClientSGId** - `{u'Ref': u'ClientSecurityGroup'}`
 * **InstanceId** - `{u'Ref': u'BastionServer'}`
 * **PublicDNS** - `{u'Fn::GetAtt': [u'BastionServer', u'PublicDnsName']}`
 * **PublicIP** - `{u'Fn::GetAtt': [u'BastionServer', u'PublicIp']}`
 * **SSMDocument** - `{u'Ref': u'SSMSetUser'}`