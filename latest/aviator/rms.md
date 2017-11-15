Rms FAWS Template
=================
rms.template - RMS 2.1 Deployment
### Parameters

#### Subnets
- Type: `List<AWS::EC2::Subnet::Id>`
- Description: `Private Subnet IDs for deployment. This is for the ALTM appliances.`

#### VPCID
- Type: `AWS::EC2::VPC::Id`
- Description: `Select Virtual Private Cloud ID.`

#### CloudTrailLogBucket
- AllowedPattern: `^[a-z0-9]+-logs$||^$`
- ConstraintDescription: `Should match the pattern '^[a-z0-9]+-logs$'.`
- Type: `String`
- Description: `The S3 bucket where Cloudtrail logs are stored.  Ignored if this is not the first RMS deployment under this account.`

#### AvailabilityZoneCount
- Default: `2`
- Type: `String`
- Description: `Number of Availability Zones (3 AZs needs a use case).`
- AllowedValues: `['1', '2', '3']`

#### VPCCIDR
- Description: `The IP address space to be used for this VPC, in CIDR notation`
- MinLength: `9`
- MaxLength: `18`
- AllowedPattern: `^([0-9]+\.){3}[0-9]+\/[0-9]+$`
- ConstraintDescription: `Must be a valid CIDR range of the form x.x.x.x/x.`
- Type: `String`

#### ThreatManagerVolumeSize
- Default: `50`
- Type: `String`
- Description: `Select EBS Volume Size in GB.`
- AllowedValues: `['40', '50', '60', '80', '100', '200', '300', '500', '1000', '1024']`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### ThreatManagerInstanceType
- Default: `c4.xlarge`
- Type: `String`
- ConstraintDescription: `Must be a valid EC2 instance type. Default is t2.micro`
- Description: `Select instance type`
- AllowedValues: `['c3.large', 'c3.xlarge', 'c3.2xlarge', 'c3.4xlarge', 'c4.large', 'c4.xlarge', 'c4.2xlarge', 'c4.4xlarge']`

#### KeyName
- Type: `AWS::EC2::KeyPair::KeyName`
- ConstraintDescription: `Must be the name of an existing EC2 KeyPair.`
- Description: `Name of an existing EC2 KeyPair to enable SSH access to the instances.`

#### InstanceRoleManagedPolicyArns
- Default: ``
- Type: `String`
- Description: `A comma delimited list of IAM policy ARNs for the InstanceRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### AlertLogicExternalId
- Default: ``
- AllowedPattern: `^[a-zA-Z0-9]{15,25}$||^$`
- Type: `String`
- Description: `A random alphanumeric string between 15 and 25 characters in length.  It must be provided to Alert Logic when creating the AWS Credentials in the Cloud Defender UI.  Omit if this is not the first RMS deployment under this account.`
- ConstraintDescription: `Must be empty or an alphanumeric string between 15-25 characters.`

#### AlertLogicDataCenter
- Default: `US`
- Type: `String`
- Description: `Alert Logic Data Center where logs will be shipped.`
- AllowedValues: `['US', 'EU']`

#### ThreatManagerBuildState
- Default: `Deploy`
- Type: `String`
- Description: `Select 'Deploy' unless the stack is being built for testing in an account without access to the Alert Logic AMIs.`
- AllowedValues: `['Deploy', 'Test']`

### Outputs
- `ConnectSQSQueue`
- `SQSQueueName`
- `LoggingCrossAccountRole`
- `AlertLogicApplianceIPs`
- `DeviceSecurityGroup`
- `AgentSecurityGroup`
- `CrossAccountRole`
- `ExternalID`

### Alarms
#### SystemRecoveryAlarm3
- Description: Status checks have failed for system, recovering instance
- Metric: StatusCheckFailed_System
- Threshold: 0
- Actions: `{'Fn::Sub': 'arn:aws:automate:${AWS::Region}:ec2:recover'}`

#### SystemRecoveryAlarm2
- Description: Status checks have failed for system, recovering instance
- Metric: StatusCheckFailed_System
- Threshold: 0
- Actions: `{'Fn::Sub': 'arn:aws:automate:${AWS::Region}:ec2:recover'}`

#### SystemRecoveryAlarm1
- Description: Status checks have failed for system, recovering instance
- Metric: StatusCheckFailed_System
- Threshold: 0
- Actions: `{'Fn::Sub': 'arn:aws:automate:${AWS::Region}:ec2:recover'}`

#### InstanceRecoveryNotification2
- Description: Status checks have failed, generating ticket.
- Metric: StatusCheckFailed_Instance
- Threshold: 0
- Actions: `{'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-emergency'}`

#### InstanceRecoveryNotification3
- Description: Status checks have failed, generating ticket.
- Metric: StatusCheckFailed_Instance
- Threshold: 0
- Actions: `{'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-emergency'}`

#### SystemRecoveryNotification2
- Description: Trigger ticket notification when instance status check fails for 10 consecutive minutes.
- Metric: StatusCheckFailed_System
- Threshold: 0
- Actions: `{'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-emergency'}`

#### SystemRecoveryNotification3
- Description: Trigger ticket notification when instance status check fails for 10 consecutive minutes.
- Metric: StatusCheckFailed_System
- Threshold: 0
- Actions: `{'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-emergency'}`

#### SystemRecoveryNotification1
- Description: Trigger ticket notification when instance status check fails for 10 consecutive minutes.
- Metric: StatusCheckFailed_System
- Threshold: 0
- Actions: `{'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-emergency'}`

#### InstanceRecoveryAlarm3
- Description: Status checks have failed, rebooting system.
- Metric: StatusCheckFailed_Instance
- Threshold: 0
- Actions: `{'Fn::Sub': 'arn:aws:swf:${AWS::Region}:${AWS::AccountId}:action/actions/AWS_EC2.InstanceId.Reboot/1.0'}`

#### InstanceRecoveryAlarm2
- Description: Status checks have failed, rebooting system.
- Metric: StatusCheckFailed_Instance
- Threshold: 0
- Actions: `{'Fn::Sub': 'arn:aws:swf:${AWS::Region}:${AWS::AccountId}:action/actions/AWS_EC2.InstanceId.Reboot/1.0'}`

#### InstanceRecoveryAlarm1
- Description: Status checks have failed, rebooting system.
- Metric: StatusCheckFailed_Instance
- Threshold: 0
- Actions: `{'Fn::Sub': 'arn:aws:swf:${AWS::Region}:${AWS::AccountId}:action/actions/AWS_EC2.InstanceId.Reboot/1.0'}`

#### InstanceRecoveryNotification1
- Description: Status checks have failed, generating ticket.
- Metric: StatusCheckFailed_Instance
- Threshold: 0
- Actions: `{'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-emergency'}`
