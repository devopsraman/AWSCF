Windowsad2016Asg FAWS Template
==============================
windowsAD_2016_asg.template - Autoscaling EC2 Instances with Rolling Updates and Notifications. **WARNING** This template creates one or more Amazon EC2  instances and an Elastic Load Balancer. You will be billed for the AWS resources used if you create a stack from this template.
### Parameters

#### ScalingCreateTimeOut
- Default: `20M`
- Type: `String`
- ConstraintDescription: `#H#M#S where each # is the number of hours or minutes or seconds`
- Description: `Time to wait for the number of signals equal to ScalingMin. H/M/S Hours/Minutes/Seconds`

#### LoadBalancerNames
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A list of Classic load balancers associated with this Auto Scaling group.`

#### CwLowOperator
- Default: `LessThanThreshold`
- Type: `String`
- Description: `Math operator used by CloudWatch for alarms and triggers.`
- AllowedValues: `['GreaterThanOrEqualToThreshold', 'GreaterThanThreshold', 'LessThanThreshold', 'LessThanOrEqualToThreshold']`

#### ASGSecurityGroupList
- Type: `List<AWS::EC2::SecurityGroup::Id>`
- Description: `A list that contains the EC2 security groups to assign to the Amazon EC2 instances in the Auto Scaling group.`

#### CwLowThreshold
- Default: `30`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `The value against which the specified statistic is compared.`
- ConstraintDescription: `Must be a valid integer.`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### ScalingUpdateTimeOut
- Default: `20M`
- Type: `String`
- ConstraintDescription: `#H#M#S where each # is the number of hours or minutes or seconds`
- Description: `Post update pause before additional Auto Scale resource changes. H/M/S Hours/Minutes/Seconds`

#### CwScalingMetric
- Default: `CPUUtilization`
- Type: `String`
- Description: `Select the metric to be used for scaling.`
- AllowedValues: `['CPUUtilization', 'NetworkIn', 'NetworkOut']`

#### EBSOptimized
- Default: `False`
- Type: `String`
- Description: `Use EBS Optimized.`
- AllowedValues: `['False', 'True']`

#### ScalingMin
- Default: `1`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `The minimum size of the Auto Scaling group.`
- ConstraintDescription: `Must be a valid integer.`

#### CWLogRetention
- Default: `30`
- Type: `String`
- ConstraintDescription: `Must be a valid integer.`
- Description: `The number of days to retain Cloudwatch Logs for this Autoscaling Group.`
- AllowedValues: `['1', '3', '5', '7', '14', '30', '60', '90', '120', '150', '180', '365', '400', '545', '731', '1827', '3653']`

#### Ebs2VolumeSize
- Default: ``
- Type: `String`
- Description: `Select Second EBS Volume Size in GB.`

#### AppSubnet
- Type: `List<AWS::EC2::Subnet::Id>`
- Description: `Subnets for Application`

#### dnsIpAddresses
- Type: `CommaDelimitedList`
- Description: `IP addresses of the Active Directory DNS servers.`

#### CwHighPeriod
- Default: `60`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `Time the specified statistic is applied. Must be in seconds that is also a multiple of 60.`
- ConstraintDescription: `Must be a valid integer.`

#### directoryName
- Type: `String`
- Description: `Full name of Active Directory Domain.`

#### EnableRackspaceTicket
- Default: `False`
- Type: `String`
- Description: `Specifies whether alarms will generate Rackspace tickets`
- AllowedValues: `['False', 'True']`

#### IopsVolume2
- Default: `0`
- Type: `Number`
- Description: `Iops value required for use with io1 on secondary EBS volumes. This value should be 3 times the secondary EBS volume size`

#### ImageId
- Default: ``
- Type: `String`
- Description: `The image ID to be used to build the Auto Scale group. OPTIONAL`

#### CwLowPeriod
- Default: `300`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `Time the specified statistic is applied. Must be in seconds that is also a multiple of 60.`
- ConstraintDescription: `Must be a valid integer.`

#### ScalingTermination
- Default: `1`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `The maximum number of instances that are terminated at a given time.`
- ConstraintDescription: `Must be a valid integer.`

#### KeyName
- ConstraintDescription: `Must be the name of an existing EC2 KeyPair.`
- Type: `AWS::EC2::KeyPair::KeyName`
- Description: `Name of an existing EC2 KeyPair to enable SSH access to the instances.`

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

#### EC2ScaleDownCooldown
- Default: `60`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `Time in seconds before any further trigger-related scaling can occur.`
- ConstraintDescription: `Must be a valid integer.`

#### InstanceType
- Default: `t2.micro`
- Type: `String`
- ConstraintDescription: `Must be a valid EC2 instance type. Default is t2.micro`
- Description: `Select instance type`
- AllowedValues: `[u't2.nano', u't2.micro', u't2.small', u't2.medium', u't2.large', u't2.xlarge', u't2.2xlarge', u'm3.medium', u'm3.large', u'm3.xlarge', u'm3.2xlarge', u'm4.large', u'm4.xlarge', u'm4.2xlarge', u'm4.4xlarge', u'm4.10xlarge', u'm4.16xlarge', u'r3.large', u'r3.xlarge', u'r3.2xlarge', u'r3.4xlarge', u'r3.8xlarge', u'r4.large', u'r4.xlarge', u'r4.2xlarge', u'r4.4xlarge', u'r4.8xlarge', u'r4.16xlarge', u'x1.16xlarge', u'x1.32xlarge', u'i2.xlarge', u'i2.2xlarge', u'i2.4xlarge', u'i2.8xlarge', u'i3.large', u'i3.xlarge', u'i3.2xlarge', u'i3.4xlarge', u'i3.8xlarge', u'i3.16xlarge', u'c3.large', u'c3.xlarge', u'c3.2xlarge', u'c3.4xlarge', u'c3.8xlarge', u'c4.large', u'c4.xlarge', u'c4.2xlarge', u'c4.4xlarge', u'c4.8xlarge', u'g2.2xlarge', u'g2.8xlarge', u'g3.4xlarge', u'g3.8xlarge', u'g3.16xlarge', u'p2.xlarge', u'p2.8xlarge', u'p2.16xlarge', u'd2.xlarge', u'd2.2xlarge', u'd2.4xlarge', u'd2.8xlarge', u'f1.2xlarge', u'f1.16xlarge']`

#### HealthCheckGracePeriod
- Default: `300`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `Number of seconds grace during which no autoscaling actions will be taken.`
- ConstraintDescription: `Must be a valid integer.`

#### Ebs2VolumeType
- Default: `gp2`
- Type: `String`
- Description: `Select EBS Volume Type.`
- AllowedValues: `['io1', 'standard', 'gp2']`

#### CwHighOperator
- Default: `GreaterThanThreshold`
- Type: `String`
- Description: `Math operator used by CloudWatch for alarms and triggers.`
- AllowedValues: `['GreaterThanOrEqualToThreshold', 'GreaterThanThreshold', 'LessThanThreshold', 'LessThanOrEqualToThreshold']`

#### TargetGroupARNs
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A list of Amazon Resource Names (ARN) of target groups to associate with the Auto Scaling group.`

#### directoryId
- Type: `String`
- Description: `Directory ID of managed Active Directory.`

#### EbsVolumeSize
- Default: `60`
- Type: `String`
- Description: `Select EBS Volume Size in GB.`

#### HealthCheckType
- Default: `EC2`
- Type: `String`
- Description: `Define the type of healthcheck for the AutoScaling group.`
- AllowedValues: `['EC2', 'ELB']`

#### EC2ScaleUpAdjustment
- Default: `1`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `Number of EC2 instances to scale up by at a time.`
- ConstraintDescription: `Must be a valid integer.`

#### CwHighThreshold
- Default: `60`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `The value against which the specified statistic is compared.`
- ConstraintDescription: `Must be a valid integer.`

#### ScalingNotificationTopic
- Default: ``
- Type: `String`
- Description: `SNS Topic ARN to notify if there are any scaling operations. OPTIONAL`

#### InstanceRoleManagedPolicyArns
- Default: ``
- Type: `String`
- Description: `A comma delimited list of IAM policy ARNs for the InstanceRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### PatchingGroupTag
- Default: ``
- Type: `String`
- Description: `Group ID to be used by System Manager for Patching (OPTIONAL)`

#### EC2ScaleDownAdjustment
- Default: `1`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `Number of EC2 instances to scale down by at a time.`
- ConstraintDescription: `Must be a valid integer.`

#### DesiredCapacity
- Default: `2`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `Specifies the desired capacity for the Auto Scaling group.`
- ConstraintDescription: `Must be a valid integer.`

#### MinInstancesInService
- Default: `0`
- Type: `Number`
- Description: `Specifies the minimum number of instances that must be in service within the Auto Scaling group while AWS CloudFormation updates old instances.`

#### SSMInventoryTag
- Default: `True`
- Type: `String`
- Description: `Determines whether Instance is tracked via System Manager Inventory.`
- AllowedValues: `['False', 'True']`

#### TerminatedInstances
- Default: `30`
- Type: `Number`
- Description: `Specifies the maximum number of instances that can be terminated in a six hour period without generating a Cloudwatch Alarm.`

#### APPGroupName
- ConstraintDescription: `Must follow normal syntax conventions.`
- Type: `String`
- Description: `EC2 Server Instance Name`

#### CwLowEvaluations
- Default: `3`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `The number of periods over which data is compared to the specified threshold.`
- ConstraintDescription: `Must be a valid integer.`

#### CwHighEvaluations
- Default: `3`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `The number of periods over which data is compared to the specified threshold.`
- ConstraintDescription: `Must be a valid integer.`

#### Iops
- Default: `0`
- Type: `Number`
- Description: `Iops value required for use with io1 EBS volumes. This value should be 3 times the EBS volume size`

#### DetailedMonitoring
- Default: `True`
- Type: `String`
- Description: `Enable Detailed Monitoring.`
- AllowedValues: `['False', 'True']`

#### EbsVolumeType
- Default: `gp2`
- Type: `String`
- Description: `Select EBS Volume Type.`
- AllowedValues: `['io1', 'standard', 'gp2']`

#### ScalingMax
- Default: `2`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `The maximum size of the Auto Scaling group.`
- ConstraintDescription: `Must be a valid integer.`

#### EC2ScaleUpCooldown
- Default: `60`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `Time in seconds before any further trigger-related scaling can occur.`
- ConstraintDescription: `Must be a valid integer.`

#### EncryptEBSVolume
- Default: `False`
- Type: `String`
- Description: `Specifies whether to encrypt the EBS volume.`
- AllowedValues: `['False', 'True']`

### Outputs
- `GroupName`

### Alarms
#### GroupTerminatingInstances
- Description: `{'Fn::Sub': 'Over ${TerminatedInstances} instances terminated in last 6 hours, generating ticket to investigate.'}`
- Metric: GroupTerminatingInstances
- Threshold: `{'Ref': 'TerminatedInstances'}`
- Actions: `{'Fn::If': ['RackspaceAlarmsEnabled', {'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-emergency'}, {'Ref': 'AWS::NoValue'}]}`

#### ScaleAlarmHigh
- Description: `{'Fn::Sub': 'Scale-up if ${CwScalingMetric} ${CwHighOperator} ${CwHighThreshold}% for ${CwHighPeriod} seconds ${CwHighEvaluations} times.'}`
- Metric: `{'Ref': 'CwScalingMetric'}`
- Threshold: `{'Ref': 'CwHighThreshold'}`
- Actions: `{'Ref': 'EC2ScaleUpPolicy'}`

#### ScaleAlarmLow
- Description: `{'Fn::Sub': 'Scale-down if ${CwScalingMetric} ${CwLowOperator} ${CwLowThreshold}% for ${CwLowPeriod} seconds ${CwLowEvaluations} times.'}`
- Metric: `{'Ref': 'CwScalingMetric'}`
- Threshold: `{'Ref': 'CwLowThreshold'}`
- Actions: `{'Ref': 'EC2ScaleDownPolicy'}`
