NavAmazonAutorecovery FAWS Template
===================================
nav_amazon_autorecovery.template - AutoRecovery EC2 Instance. **WARNING** You will be billed for the AWS resources used if you create a stack from this template.
### Parameters

#### InternalRecordName
- Default: ``
- Type: `String`
- Description: `Record Name for the new Resource Record in the Internal Hosted Zone`

#### SSMInventoryTag
- Default: `True`
- Type: `String`
- Description: `Determines whether Instance is tracked via System Manager Inventory.`
- AllowedValues: `['False', 'True']`

#### ARInstanceName
- Type: `String`
- ConstraintDescription: `Must follow normal syntax conventions.`
- Description: `EC2 Server Instance Name`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### CwCpuHighOperator
- Default: `GreaterThanThreshold`
- Type: `String`
- Description: `Math operator used by CloudWatch for alarms and triggers.`
- AllowedValues: `['GreaterThanOrEqualToThreshold', 'GreaterThanThreshold', 'LessThanThreshold', 'LessThanOrEqualToThreshold']`

#### CwCpuHighThreshold
- AllowedPattern: `([0-9]+)`
- Default: `90`
- Type: `String`
- Description: `The value against which the specified statistic is compared.`
- ConstraintDescription: `Must be a valid integer.`

#### Ebs2MountPoint
- Default: ``
- Type: `String`
- Description: `Filesystem Mount point for 2nd EBS volume.  Omit to prevent changes to 2nd volume.`

#### CWLogRetention
- Default: `30`
- Type: `String`
- ConstraintDescription: `Must be a valid integer.`
- Description: `The number of days to retain Cloudwatch Logs for this instance.`
- AllowedValues: `['1', '3', '5', '7', '14', '30', '60', '90', '120', '150', '180', '365', '400', '545', '731', '1827', '3653']`

#### Ebs2VolumeSize
- Default: ``
- Type: `String`
- Description: `Select Second EBS Volume Size in GB.`

#### ImageId
- Default: ``
- Type: `String`
- Description: `The image ID to be used to build the EC2 Instance. OPTIONAL`

#### IopsVolume2
- Default: `0`
- Type: `Number`
- Description: `IOPS value required for use with io1 on secondary EBS volumes. This value should be 3 times the secondary EBS volume size`

#### AppSubnet
- Type: `AWS::EC2::Subnet::Id`
- Description: `Subnets for Application`

#### InternalZoneName
- Default: ``
- Type: `String`
- Description: `TLD for Internal Hosted Zone`

#### Iops
- Default: `0`
- Type: `Number`
- Description: `Iops value required for use with io1 EBS volumes. This value should be 3 times the EBS volume size`

#### CwCpuHighPeriod
- AllowedPattern: `([0-9]+)`
- Default: `60`
- Type: `String`
- Description: `Time the specified statistic is applied. Must be in seconds that is also a multiple of 60.`
- ConstraintDescription: `Must be a valid integer.`

#### PlacementTenancy
- Default: `default`
- Type: `String`
- Description: `The placement tenancy for EC2 devices`
- AllowedValues: `['dedicated', 'default', 'host']`

#### SnapshotId
- Default: ``
- Type: `String`
- Description: `The Snapshot ID to be used to build the 2nd EBS volume. OPTIONAL`

#### BackupsEnabled
- Default: `False`
- Type: `String`
- Description: `Value of the 'Backup' tag, used to assign the EBSSnapper configuration.`

#### EIPAllocationId
- Default: ``
- Type: `String`
- Description: `The AllocationId of the EIP you want to associate with the instance (optional).`

#### InstanceType
- Default: `t2.micro`
- Type: `String`
- ConstraintDescription: `Must be a valid EC2 instance type. Default is t2.micro`
- Description: `Select instance type`
- AllowedValues: `[u't2.nano', u't2.micro', u't2.small', u't2.medium', u't2.large', u't2.xlarge', u't2.2xlarge', u'm3.medium', u'm3.large', u'm3.xlarge', u'm3.2xlarge', u'm4.large', u'm4.xlarge', u'm4.2xlarge', u'm4.4xlarge', u'm4.10xlarge', u'm4.16xlarge', u'r3.large', u'r3.xlarge', u'r3.2xlarge', u'r3.4xlarge', u'r3.8xlarge', u'r4.large', u'r4.xlarge', u'r4.2xlarge', u'r4.4xlarge', u'r4.8xlarge', u'r4.16xlarge', u'x1.16xlarge', u'x1.32xlarge', u'i2.xlarge', u'i2.2xlarge', u'i2.4xlarge', u'i2.8xlarge', u'i3.large', u'i3.xlarge', u'i3.2xlarge', u'i3.4xlarge', u'i3.8xlarge', u'i3.16xlarge', u'c3.large', u'c3.xlarge', u'c3.2xlarge', u'c3.4xlarge', u'c3.8xlarge', u'c4.large', u'c4.xlarge', u'c4.2xlarge', u'c4.4xlarge', u'c4.8xlarge', u'g2.2xlarge', u'g2.8xlarge', u'g3.4xlarge', u'g3.8xlarge', u'g3.16xlarge', u'p2.xlarge', u'p2.8xlarge', u'p2.16xlarge', u'd2.xlarge', u'd2.2xlarge', u'd2.4xlarge', u'd2.8xlarge', u'f1.2xlarge', u'f1.16xlarge']`

#### Ebs2VolumeType
- Default: `gp2`
- Type: `String`
- Description: `Select EBS Volume Type.`
- AllowedValues: `['io1', 'standard', 'gp2']`

#### EbsVolumeSize
- Default: `60`
- Type: `String`
- Description: `Select EBS Volume Size in GB.`

#### KeyName
- ConstraintDescription: `Must be the name of an existing EC2 KeyPair.`
- Type: `AWS::EC2::KeyPair::KeyName`
- Description: `Name of an existing EC2 KeyPair to enable SSH access to the instances.`

#### NotificationTopic
- Default: ``
- Type: `String`
- Description: `SNS Topic ARN to notify if there are any alarms. OPTIONAL`

#### InstanceRoleManagedPolicyArns
- Default: ``
- Type: `String`
- Description: `A comma delimited list of IAM policy ARNs for the InstanceRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### PatchingGroupTag
- Default: ``
- Type: `String`
- Description: `Group ID to be used by System Manager for Patching (OPTIONAL)`

#### ARInstanceSecurityGroupList
- Type: `List<AWS::EC2::SecurityGroup::Id>`
- Description: `A list that contains the EC2 security groups to assign to the Amazon EC2 instance`

#### CreationPolicyTimeOut
- Default: `20M`
- ConstraintDescription: `#H#M#S where each # is the number of hours or minutes or seconds`
- Type: `String`
- Description: `Time to wait for the number of signals for the creation policy. H/M/S Hours/Minutes/Seconds`

#### EBSOptimized
- Default: `False`
- Type: `String`
- Description: `Use EBS Optimized.`
- AllowedValues: `['False', 'True']`

#### DetailedMonitoring
- Default: `True`
- Type: `String`
- Description: `Enable Detailed Monitoring.`
- AllowedValues: `['False', 'True']`

#### CwCpuHighEvaluations
- AllowedPattern: `([0-9]+)`
- Default: `15`
- Type: `String`
- Description: `The number of periods over which data is compared to the specified threshold.`
- ConstraintDescription: `Must be a valid integer.`

#### EbsVolumeType
- Default: `gp2`
- Type: `String`
- Description: `Select EBS Volume Type.`
- AllowedValues: `['io1', 'standard', 'gp2']`

#### DisableApiTermination
- Default: `False`
- Type: `String`
- Description: `Specifies whether the instance can be terminated through the API.`
- AllowedValues: `['False', 'True']`

#### InternalZoneId
- Default: ``
- Type: `String`
- Description: `The Route53 Internal Hosted Zone ID`

#### EncryptEBSVolume
- Default: `False`
- Type: `String`
- Description: `Specifies whether to encrypt the EBS volume.`
- AllowedValues: `['False', 'True']`

### Outputs

### Alarms
#### StatusCheckFailedSystemAlarmRecover
- Description: Status checks have failed for system, recovering instance
- Metric: StatusCheckFailed_System
- Threshold: 0
- Actions: `{'Fn::Sub': 'arn:aws:automate:${AWS::Region}:ec2:recover'}`

#### StatusCheckFailedSystemAlarmTicket
- Description: Status checks have failed for system, generating ticket.
- Metric: StatusCheckFailed_System
- Threshold: 0
- Actions: `{'Fn::If': ['isNotification', {'Ref': 'NotificationTopic'}, {'Ref': 'AWS::NoValue'}]}`

#### StatusCheckFailedInstanceAlarmReboot
- Description: Status checks have failed, rebooting system.
- Metric: StatusCheckFailed_Instance
- Threshold: 0
- Actions: `{'Fn::Sub': 'arn:aws:swf:${AWS::Region}:${AWS::AccountId}:action/actions/AWS_EC2.InstanceId.Reboot/1.0'}`

#### CPUAlarmHigh
- Description: `{'Fn::Sub': 'CPU Alarm ${CwCpuHighOperator} ${CwCpuHighThreshold}% for ${CwCpuHighPeriod} seconds ${CwCpuHighEvaluations} times.'}`
- Metric: CPUUtilization
- Threshold: `{'Ref': 'CwCpuHighThreshold'}`
- Actions: `{'Fn::If': ['isNotification', {'Ref': 'NotificationTopic'}, {'Ref': 'AWS::NoValue'}]}`

#### StatusCheckFailedInstanceAlarmTicket
- Description: Status checks have failed, generating ticket.
- Metric: StatusCheckFailed_Instance
- Threshold: 0
- Actions: `{'Fn::If': ['isNotification', {'Ref': 'NotificationTopic'}, {'Ref': 'AWS::NoValue'}]}`
