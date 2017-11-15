RdsPostgres FAWS Template
=========================
rds_postgres.template - Creates the necessary resources for an RDS instance. Please be aware that this template will create resources for which you will be charged.
### Parameters

#### InternalRecordName
- Default: ``
- Type: `String`
- Description: `Record Name for the new Resource Record in the Internal Hosted Zone`

#### DBNameVersion
- Default: `v00`
- Type: `String`
- Description: `NOTE: This needs to increment on update with new snapshot`

#### PubliclyAccessible
- Default: `False`
- ConstraintDescription: `Must be either True or False.`
- Type: `String`
- Description: `Indicates whether the database instance is an Internet-facing instance.`
- AllowedValues: `['True', 'False']`

#### MasterUsername
- Type: `String`
- Description: `The name of master user for the client DB instance.`
- MinLength: `1`
- AllowedPattern: `^[^\d][a-zA-Z0-9_]+?$`
- MaxLength: `63`
- ConstraintDescription: `Must be between 1 and 63 characters and begin with a letter.`

#### NotificationTopic
- Default: ``
- Type: `String`
- Description: `SNS Topic ARN to notify if there are any alarms. (OPTIONAL)`

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
- Default: `100`
- Type: `Number`
- Description: `CloudWatch Write IOPSLimit Threshold`

#### RDSVolumeType
- Default: `gp2`
- Type: `String`
- Description: `Select RDS Volume Type.`
- AllowedValues: `['io1', 'standard', 'gp2']`

#### Engine
- Default: `postgres`
- Type: `String`
- Description: `Database Engine Type.`
- AllowedValues: `['postgres']`

#### PreferredBackupWindow
- Default: `05:00-06:00`
- AllowedPattern: `^[0-9]{2}:[0-9]{2}-[0-9]{2}:[0-9]{2}$`
- Type: `String`
- Description: `The daily time range during which automated backups are created if automated backups are enabled.`
- ConstraintDescription: `Must be in the format hh24:mi-hh24:mi`

#### EventCategories
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A list of RDS event categories.  Submissions will be made to the provided NotificationTopic for each matching event. Acceptable values can be found with the CLI command 'aws rds describe-event-categories' (OPTIONAL)`

#### MajorEngineVersion
- Default: `9.6`
- Type: `String`
- Description: `Database Engine Major Version`
- AllowedValues: `[u'9.4', u'9.5', u'9.6', u'9.3']`

#### MinorEngineVersion
- Default: `9.6.5`
- Type: `String`
- Description: `Database Engine Minor Version http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_CreateDBInstance.html`
- AllowedValues: `[u'9.4.9', u'9.3.19', u'9.6.1', u'9.3.12', u'9.3.17', u'9.3.16', u'9.4.7', u'9.4.12', u'9.5.4', u'9.5.7', u'9.4.11', u'9.4.14', u'9.5.2', u'9.6.2', u'9.6.3', u'9.3.14', u'9.5.9', u'9.5.6', u'9.6.5']`

#### AutoMinorVersionUpgrade
- Default: `True`
- ConstraintDescription: `Must be either True or False.`
- Type: `String`
- Description: `Indicates that minor engine upgrades will be applied automatically to the DB instance during the maintenance window.`
- AllowedValues: `['True', 'False']`

#### InternalZoneName
- Default: ``
- Type: `String`
- Description: `TLD for Internal Hosted Zone`

#### ParameterGroupFamily
- Default: `postgres9.6`
- Type: `String`
- Description: `Parameter Group Family Name (ex. mysql5.7,sqlserver-se-12.0,postgres9.5,oracle-se-12.1,mariadb10.1)`
- AllowedValues: `[u'postgres9.6', u'postgres9.5', u'postgres9.4', u'postgres9.3']`

#### RDSVolumeSize
- Description: `Select RDS Volume Size in GB.`
- Default: `10`
- Type: `Number`
- MaxValue: `6144`
- MinValue: `5`
- ConstraintDescription: `Must be between 5 and 6144`

#### CWFreeStorageSpaceLimit
- Default: `1024000000`
- Type: `Number`
- Description: `CloudWatch Free Storage Space Limit Threshold (Bytes)`

#### CWReadIopsLimit
- Default: `100`
- Type: `Number`
- Description: `CloudWatch Read IOPSLimit Threshold`

#### BackupRetentionPeriod
- Description: `The number of days for which automated backups are retained. Setting this parameter to a positive number enables backups. Setting this parameter to 0 disables automated backups. Compass best practice is 30 or more days.`
- Default: `35`
- Type: `Number`
- MaxValue: `35`
- MinValue: `0`
- ConstraintDescription: `Must be between 0 and 35.`

#### DBName
- Type: `String`
- Description: `The meaning of this parameter differs according to the database engine you use.`
- Default: `MyRDS`
- MinLength: `0`
- MaxLength: `63`
- ConstraintDescription: `String length must be between 0 and 63.`

#### PreferredMaintenanceWindow
- Default: `Sun:07:00-Sun:08:00`
- AllowedPattern: `^(Mon|Tue|Wed|Thu|Fri|Sat|Sun):[0-9]{2}:[0-9]{2}-(Mon|Tue|Wed|Thu|Fri|Sat|Sun):[0-9]{2}:[0-9]{2}$`
- Type: `String`
- Description: `The daily time range during which automated backups are created if automated backups are enabled.`
- ConstraintDescription: `Must be in the format ddd:hh24:mi-ddd:hh24:mi`

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
- Description: `Subnets for RDS Instances`

#### RDSVolumeIops
- Default: `0`
- Type: `Number`
- Description: `Iops value required for use. Typically 3 x Volume Size`

#### ExistingSubnetGroup
- Default: ``
- Type: `String`
- Description: `The existing DB subnet group to use for this instance. (OPTIONAL)`

#### MasterUserPassword
- ConstraintDescription: `Must be between 1 and 128 characters and cannot contain '@', '"', or '\/'.`
- Description: `Password for the local administrator account. Must be at least 8 characters containing letters, numbers and symbols.`
- MinLength: `8`
- AllowedPattern: `^[\p{ASCII}&&[^@\s\/"]]+$||^$`
- NoEcho: `True`
- MaxLength: `128`
- Type: `String`

#### DBSnapshotName
- Default: ``
- Type: `String`
- Description: `The name of a DB snapshot (optional).`

#### StorageEncrypted
- Default: `False`
- ConstraintDescription: `Must be either True or False.`
- Type: `String`
- Description: `Specifies whether the DB instance is encrypted.`
- AllowedValues: `['True', 'False']`

#### DBInstanceClass
- Default: `db.m3.xlarge`
- ConstraintDescription: `Must select a valid database instance type.`
- Type: `String`
- Description: `The database instance type.`
- AllowedValues: `['db.t2.micro', 'db.t2.small', 'db.t2.medium', 'db.t2.large', 'db.r3.large', 'db.r3.xlarge', 'db.r3.2xlarge', 'db.r3.4xlarge', 'db.r3.8xlarge', 'db.m3.medium', 'db.m3.large', 'db.m3.xlarge', 'db.m3.2xlarge', 'db.m4.large', 'db.m4.xlarge', 'db.m4.2xlarge', 'db.m4.4xlarge', 'db.m4.10xlarge']`

#### InternalZoneId
- Default: ``
- Type: `String`
- Description: `The Route53 Internal Hosted Zone ID`

#### Port
- Description: `The port number on which the database accepts connections.`
- Default: `5432`
- Type: `Number`
- MaxValue: `65535`
- MinValue: `1150`
- ConstraintDescription: `Must be between 1150 and 65535.`

#### DBInstanceIdentifier
- Default: ``
- Type: `String`
- Description: `The DB instance identifier. This parameter is stored as a lowercase string. (optional)`

### Outputs
- `JDBCConnectionString`
- `DBPort`
- `RDSEndpoint`
- `DBInstanceIdentifier`
- `DBAddress`

### Alarms
#### FreeStorageSpaceEmail
- Description: Free storage space has fallen below threshold, sending email notification.
- Metric: FreeStorageSpace
- Threshold: 3072000000
- Actions: `{'Fn::If': ['isNotification', {'Ref': 'NotificationTopic'}, {'Ref': 'AWS::NoValue'}]}`

#### WriteIOPSHigh
- Description: `{'Fn::Sub': 'Alarm if ${RDSInstance} WriteIOPs > ${CWWriteIopsLimit} for 5 minutes'}`
- Metric: WriteIOPS
- Threshold: `{'Ref': 'CWWriteIopsLimit'}`
- Actions: `{'Fn::If': ['isNotification', {'Ref': 'NotificationTopic'}, {'Ref': 'AWS::NoValue'}]}`

#### CPUAlarmHigh
- Description: `{'Fn::Sub': 'Alarm if ${RDSInstance} CPU > ${CWCPUThreshold}% for 5 minutes'}`
- Metric: CPUUtilization
- Threshold: `{'Ref': 'CWCPUThreshold'}`
- Actions: `{'Fn::If': ['isNotification', {'Ref': 'NotificationTopic'}, {'Ref': 'AWS::NoValue'}]}`

#### ReadIOPSHigh
- Description: `{'Fn::Sub': 'Alarm if ${RDSInstance} ReadIOPs > ${CWReadIopsLimit} for 5 minutes'}`
- Metric: ReadIOPS
- Threshold: `{'Ref': 'CWReadIopsLimit'}`
- Actions: `{'Fn::If': ['isNotification', {'Ref': 'NotificationTopic'}, {'Ref': 'AWS::NoValue'}]}`

#### FreeStorageSpaceTicket
- Description: Free storage space has fallen below threshold, generating ticket.
- Metric: FreeStorageSpace
- Threshold: `{'Ref': 'CWFreeStorageSpaceLimit'}`
- Actions: ["`{'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-urgent'}`", "`{'Fn::If': ['isNotification', {'Ref': 'NotificationTopic'}, {'Ref': 'AWS::NoValue'}]}`"]
