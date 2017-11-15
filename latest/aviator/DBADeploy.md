Dbadeploy FAWS Template
=======================
DBADeploy.template - Deploy RDBA workstation to access RDS instances.
### Parameters

#### EC2Subnets
- Type: `List<AWS::EC2::Subnet::Id>`
- Description: `Subnet where the instance will be deployed`

#### VPCID
- Type: `AWS::EC2::VPC::Id`
- Description: `VPC to deploy EC2 instance.`

#### ScalingTimeOut
- Default: `30M`
- Type: `String`
- ConstraintDescription: `#H#M#S where each # is the number of hours or minutes or seconds`
- Description: `Time to wait for the number of signals equal to ScalingMin. H/M/S Hours/Minutes/Seconds`

#### EbsVolumeSize
- Default: `60`
- Type: `Number`
- Description: `Select EBS Volume Size in GB.`
- MinValue: `0`

#### LinuxWorkstation
- Default: `None`
- Type: `String`
- Description: `Deploy a Linux Workstation`
- AllowedValues: `['Deploy', 'None']`

#### DbConnectLambdaRoleManagedPolicyArns
- Default: ``
- Type: `String`
- Description: `A comma delimited list of IAM policy ARNs for the DbConnectLambdaRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### InstanceRoleManagedPolicyArns
- Default: ``
- Type: `String`
- Description: `A comma delimited list of IAM policy ARNs for the InstanceRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### ScalingTermination
- Default: `1`
- ConstraintDescription: `Must be a valid integer.`
- Type: `Number`
- Description: `The maximum number of instances that are terminated at a given time.`
- MinValue: `1`

#### LambdaFunctionName
- Default: `DBATagSupport`
- Type: `String`
- Description: `The name to assign to the Lambda Function`

#### KeyName
- ConstraintDescription: `Must be the name of an existing EC2 KeyPair.`
- Type: `AWS::EC2::KeyPair::KeyName`
- Description: `Provides the name of the EC2 key pair.`

#### ScalingMin
- Default: `1`
- ConstraintDescription: `Must be a valid integer.`
- Type: `Number`
- Description: `The minimum size of the Auto Scaling group.`
- MinValue: `0`

#### ScalingMax
- Default: `1`
- ConstraintDescription: `Must be a valid integer.`
- Type: `Number`
- Description: `The maximum size of the Auto Scaling group.`
- MinValue: `0`

#### InstanceType
- Default: `t2.micro`
- Type: `String`
- ConstraintDescription: `Must be a valid EC2 instance type. Default is t2.micro`
- Description: `EC2 instance type.`
- AllowedValues: `[u't2.nano', u't2.micro', u't2.small', u't2.medium', u't2.large', u't2.xlarge', u't2.2xlarge', u'm3.medium', u'm3.large', u'm3.xlarge', u'm3.2xlarge', u'm4.large', u'm4.xlarge', u'm4.2xlarge', u'm4.4xlarge', u'm4.10xlarge', u'm4.16xlarge', u'r3.large', u'r3.xlarge', u'r3.2xlarge', u'r3.4xlarge', u'r3.8xlarge', u'r4.large', u'r4.xlarge', u'r4.2xlarge', u'r4.4xlarge', u'r4.8xlarge', u'r4.16xlarge', u'x1.16xlarge', u'x1.32xlarge', u'i2.xlarge', u'i2.2xlarge', u'i2.4xlarge', u'i2.8xlarge', u'i3.large', u'i3.xlarge', u'i3.2xlarge', u'i3.4xlarge', u'i3.8xlarge', u'i3.16xlarge', u'c3.large', u'c3.xlarge', u'c3.2xlarge', u'c3.4xlarge', u'c3.8xlarge', u'c4.large', u'c4.xlarge', u'c4.2xlarge', u'c4.4xlarge', u'c4.8xlarge', u'g2.2xlarge', u'g2.8xlarge', u'g3.4xlarge', u'g3.8xlarge', u'g3.16xlarge', u'p2.xlarge', u'p2.8xlarge', u'p2.16xlarge', u'd2.xlarge', u'd2.2xlarge', u'd2.4xlarge', u'd2.8xlarge', u'f1.2xlarge', u'f1.16xlarge']`

#### WindowsWorkstation
- Default: `None`
- Type: `String`
- Description: `Deploy a Windows Workstation`
- AllowedValues: `['Deploy', 'None']`

### Outputs

### Alarms