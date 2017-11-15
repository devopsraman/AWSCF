Aurora FAWS Template
====================
aurora.template - Creates the necessary resources for an RDS instance. Please be aware that this template will create resources for which you will be charged.
### Parameters

#### InternalRecordName
- Default: ``
- Type: `String`
- Description: `Record Name for the new Resource Record in the Internal Hosted Zone`

#### PubliclyAccessible
- Default: `False`
- ConstraintDescription: `Must be either True or False.`
- Type: `String`
- Description: `Indicates whether the database instance is an Internet-facing instance.`
- AllowedValues: `['True', 'False']`

#### MasterUsername
- AllowedPattern: `^[^\d][a-zA-Z0-9]+?$`
- MinLength: `1`
- Type: `String`
- Description: `The name of master user for the client DB instance.`
- MaxLength: `64`

#### VPCSecurityGroupIds
- Default: ``
- Type: `List<AWS::EC2::SecurityGroup::Id>`
- Description: `Existing security groups being used by App ec2 instances. If no AppSG, enter the VPC Default.`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### CWWriteIopsLimit
- Default: `100000`
- Type: `Number`
- Description: `CloudWatch Write IOPSLimit Threshold`

#### DBSnapshotARN
- Default: ``
- Type: `String`
- Description: `The identifier for the DB cluster snapshot from which you want to restore.`

#### EnableRackspaceTicket
- Default: `False`
- Type: `String`
- Description: `Specifies whether alarms will generate Rackspace tickets`
- AllowedValues: `['False', 'True']`

#### InternalZoneName
- Default: ``
- Type: `String`
- Description: `TLD for Internal Hosted Zone`

#### AutoMinorVersionUpgrade
- Default: `True`
- ConstraintDescription: `Must be either True or False.`
- Type: `String`
- Description: `Indicates that minor engine upgrades will be applied automatically to the DB instance during the maintenance window.`
- AllowedValues: `['True', 'False']`

#### PreferredBackupWindow
- Default: `05:00-06:00`
- Type: `String`
- Description: `The daily time range during which automated backups are created if automated backups are enabled.`

#### CWReadIopsLimit
- Default: `100000`
- Type: `Number`
- Description: `CloudWatch Read IOPSLimit Threshold`

#### BackupRetentionPeriod
- Description: `The number of days for which automated backups are retained. Setting this parameter to a positive number enables backups. Setting this parameter to 0 disables automated backups.`
- Default: `1`
- Type: `Number`
- MaxValue: `35`
- MinValue: `0`
- ConstraintDescription: `Must be between 0 and 35`

#### PreferredMaintenanceWindow
- Default: `Sun:07:00-Sun:08:00`
- Type: `String`
- Description: `The weekly time range (in UTC) during which system maintenance can occur.`

#### MultiAZ
- Default: `True`
- ConstraintDescription: `Must be either True or False.`
- Type: `String`
- Description: `Create a multi-AZ RDS database instance`
- AllowedValues: `['True', 'False']`

#### CWCPUThreshold
- Default: `60`
- Type: `Number`
- Description: `CloudWatch CPUUtilization Threshold`

#### RDSSubnets
- Type: `List<AWS::EC2::Subnet::Id>`
- Description: `Subnets for RDS Instances. Required 2 Subnets even for singleAZ.`

#### NotificationTopic
- Default: ``
- Type: `String`
- Description: `SNS Topic ARN to notify if there are any alarms. OPTIONAL`

#### MasterUserPassword
- Description: `Password for the local administrator account. Must be at least 8 characters containing letters, numbers and symbols.`
- MinLength: `8`
- AllowedPattern: `^[\p{ASCII}&&[^@\s\/"]]+$||^$`
- NoEcho: `True`
- MaxLength: `41`
- Type: `String`

#### StorageEncrypted
- Default: `False`
- ConstraintDescription: `Must be either True or False.`
- Type: `String`
- Description: `Specifies whether the DB instance is encrypted.`
- AllowedValues: `['True', 'False']`

#### DBInstanceClass
- Default: `db.r3.large`
- ConstraintDescription: `Must select a valid database instance type.`
- Type: `String`
- Description: `The database instance type`
- AllowedValues: `['db.t2.small', 'db.t2.medium', 'db.r3.large', 'db.r3.xlarge', 'db.r3.2xlarge', 'db.r3.4xlarge', 'db.r3.8xlarge']`

#### InternalZoneId
- Default: ``
- Type: `String`
- Description: `The Route53 Internal Hosted Zone ID`

#### Port
- Description: `The port number on which the database accepts connections.`
- Default: `3306`
- Type: `Number`
- MaxValue: `65535`
- MinValue: `1150`
- ConstraintDescription: `Must be between 1150 and 65535`

#### DBInstanceIdentifier
- Default: `Aurora`
- Type: `String`
- Description: `The DB instance identifier. This parameter is stored as a lowercase string.`

### Outputs
- `ClusterAddress`
- `DBPort`

### Alarms
#### WriteIOHigh
- Description: `{'Fn::Sub': 'Alarm if ${RDSCluster} Write IO > ${CWWriteIopsLimit} for 30 minutes'}`
- Metric: VolumeWriteIOPs
- Threshold: `{'Ref': 'CWWriteIopsLimit'}`
- Actions: `{'Fn::If': ['isNotification', {'Ref': 'NotificationTopic'}, {'Ref': 'AWS::NoValue'}]}`

#### ReadIOHigh
- Description: `{'Fn::Sub': 'Alarm if ${RDSCluster} Read IO > ${CWReadIopsLimit} for 30 minutes'}`
- Metric: VolumeReadIOPs
- Threshold: `{'Ref': 'CWReadIopsLimit'}`
- Actions: `{'Fn::If': ['isNotification', {'Ref': 'NotificationTopic'}, {'Ref': 'AWS::NoValue'}]}`

#### CPUAlarmHigh02
- Description: `{'Fn::Sub': 'Alarm if ${DBInstanceIdentifier} CPU > ${CWCPUThreshold}% for 15 minutes'}`
- Metric: CPUUtilization
- Threshold: `{'Ref': 'CWCPUThreshold'}`
- Actions: ["`{'Fn::If': ['RackspaceAlarmsEnabled', {'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-urgent'}, {'Ref': 'AWS::NoValue'}]}`", "`{'Fn::If': ['isNotification', {'Ref': 'NotificationTopic'}, {'Ref': 'AWS::NoValue'}]}`"]

#### CPUAlarmHigh01
- Description: `{'Fn::Sub': 'Alarm if ${DBInstanceIdentifier} CPU > ${CWCPUThreshold}% for 15 minutes'}`
- Metric: CPUUtilization
- Threshold: `{'Ref': 'CWCPUThreshold'}`
- Actions: ["`{'Fn::If': ['RackspaceAlarmsEnabled', {'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-urgent'}, {'Ref': 'AWS::NoValue'}]}`", "`{'Fn::If': ['isNotification', {'Ref': 'NotificationTopic'}, {'Ref': 'AWS::NoValue'}]}`"]
