WindowsBastion FAWS Template
============================
windows_bastion.template - Build an AWS User Jumpbox for RDP access.
### Parameters

#### EC2Subnets
- Type: `List<AWS::EC2::Subnet::Id>`
- Description: `Subnet where the instance will be deployed`

#### VPCID
- Type: `AWS::EC2::VPC::Id`
- Description: `VPC to deploy EC2 instance.`

#### TargetSecurityGroupId
- Type: `AWS::EC2::SecurityGroup::Id`
- Description: `Id of the Security Group containing the EC2 instance you want access to.`

#### InstanceRoleManagedPolicyArns
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A comma delimited list of IAM policy ARNs for the InstanceRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### KeyName
- ConstraintDescription: `Must be the name of an existing EC2 KeyPair.`
- Type: `AWS::EC2::KeyPair::KeyName`
- Description: `Provides the name of the EC2 key pair.`

#### BastionType
- Default: `Rackspace`
- Type: `String`
- Description: `EC2 instance type.`
- AllowedValues: `['Rackspace', 'Customer', 'Custom']`

#### InstanceType
- Default: `t2.small`
- Type: `String`
- ConstraintDescription: `Must be a valid EC2 instance type. Default is t2.small`
- Description: `EC2 instance type.`
- AllowedValues: `[u't2.nano', u't2.micro', u't2.small', u't2.medium', u't2.large', u't2.xlarge', u't2.2xlarge', u'm3.medium', u'm3.large', u'm3.xlarge', u'm3.2xlarge', u'm4.large', u'm4.xlarge', u'm4.2xlarge', u'm4.4xlarge', u'm4.10xlarge', u'm4.16xlarge', u'r3.large', u'r3.xlarge', u'r3.2xlarge', u'r3.4xlarge', u'r3.8xlarge', u'r4.large', u'r4.xlarge', u'r4.2xlarge', u'r4.4xlarge', u'r4.8xlarge', u'r4.16xlarge', u'x1.16xlarge', u'x1.32xlarge', u'i2.xlarge', u'i2.2xlarge', u'i2.4xlarge', u'i2.8xlarge', u'i3.large', u'i3.xlarge', u'i3.2xlarge', u'i3.4xlarge', u'i3.8xlarge', u'i3.16xlarge', u'c3.large', u'c3.xlarge', u'c3.2xlarge', u'c3.4xlarge', u'c3.8xlarge', u'c4.large', u'c4.xlarge', u'c4.2xlarge', u'c4.4xlarge', u'c4.8xlarge', u'g2.2xlarge', u'g2.8xlarge', u'g3.4xlarge', u'g3.8xlarge', u'g3.16xlarge', u'p2.xlarge', u'p2.8xlarge', u'p2.16xlarge', u'd2.xlarge', u'd2.2xlarge', u'd2.4xlarge', u'd2.8xlarge', u'f1.2xlarge', u'f1.16xlarge']`

#### StageOrBuild
- Default: `Build`
- Type: `String`
- Description: `Stage or Build Bastion?`
- AllowedValues: `['Stage', 'Build']`

### Outputs

### Alarms