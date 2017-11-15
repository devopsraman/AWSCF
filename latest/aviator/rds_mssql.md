RdsMssql FAWS Template
======================
rds_mssql.template - Creates the necessary resources for an RDS instance. Please be aware that this template will create resources for which you will be charged.
### Parameters

#### DirectoryId
- Default: ``
- Type: `String`
- Description: `Input the Id of the AWS Directory to join the RDS Instance to. (optional)`

#### S3BackupKMSARN
- Default: ``
- Type: `String`
- Description: `KMS Key Arn to use when encrypting/decrypting SQL backups. (OPTIONAL)`

#### InternalRecordName
- Default: ``
- Type: `String`
- Description: `Record Name for the new Resource Record in the Internal Hosted Zone`

#### DBNameVersion
- Default: `v00`
- Type: `String`
- Description: `NOTE: This needs to increment on update with new snapshot`

#### S3BackupBucketName
- Default: ``
- Type: `String`
- Description: `Name of the S3 bucket to use for SQL backups. (OPTIONAL)`

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
- MaxLength: `128`
- ConstraintDescription: `Must be between 1 and 128 characters and begin with a letter.`

#### NotificationTopic
- Default: ``
- Type: `String`
- Description: `SNS Topic ARN to notify if there are any alarms. (OPTIONAL)`

#### LicenseModel
- Type: `String`
- ConstraintDescription: `Value must be one of 'license-included' or 'bring-your-own-license'`
- Description: `Select a License Model of 'license-included' or 'bring-your-own-license'.  Changing this arameter will cause the RDS instance to be replaced.`
- AllowedValues: `['license-included', 'bring-your-own-license']`

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
- Default: `sqlserver-se`
- Type: `String`
- Description: `Database Engine Type.`
- AllowedValues: `['sqlserver-se', 'sqlserver-ee', 'sqlserver-ex', 'sqlserver-web']`

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
- Default: `13.00`
- Type: `String`
- Description: `Database Engine Major Version`
- AllowedValues: `[u'12.00', u'13.00', u'10.50', u'11.00']`

#### MinorEngineVersion
- Default: `13.00.4422.0.v1`
- Type: `String`
- Description: `Database Engine Minor Version http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_CreateDBInstance.html`
- AllowedValues: `[u'10.50.6000.34.v1', u'12.00.5000.0.v1', u'13.00.2164.0.v1', u'13.00.4422.0.v1', u'11.00.6594.0.v1', u'11.00.5058.0.v1', u'11.00.2100.60.v1', u'11.00.6020.0.v1', u'10.50.2789.0.v1', u'12.00.5546.0.v1', u'10.50.6529.0.v1', u'12.00.4422.0.v1']`

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
- Default: `sqlserver-se-13.0`
- Type: `String`
- Description: `Parameter Group Family Name (ex. mysql5.7,sqlserver-se-12.0,postgres9.5,oracle-se-12.1,mariadb10.1)`
- AllowedValues: `[u'sqlserver-se-12.0', u'sqlserver-ex-12.0', u'sqlserver-web-11.0', u'sqlserver-ee-10.5', u'sqlserver-ex-13.0', u'sqlserver-se-11.0', u'sqlserver-web-10.5', u'sqlserver-ee-11.0', u'sqlserver-ex-10.5', u'sqlserver-web-13.0', u'sqlserver-se-10.5', u'sqlserver-web-12.0', u'sqlserver-ee-13.0', u'sqlserver-ex-11.0', u'sqlserver-se-13.0', u'sqlserver-ee-12.0']`

#### RDSVolumeSize
- Description: `Select RDS Volume Size in GB.`
- Default: `200`
- Type: `Number`
- MaxValue: `4096`
- MinValue: `20`
- ConstraintDescription: `Must be between 20 and 4096`

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
- Default: ``
- MinLength: `0`
- MaxLength: `0`
- ConstraintDescription: `String must be empty.`

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

#### S3BackupPrefix
- Default: ``
- Type: `String`
- Description: `Prefix within the S3 bucket to use for SQL backups.  Used to limit access within the bucket. (OPTIONAL)`

#### RDSVolumeIops
- Default: `0`
- Type: `Number`
- Description: `Iops value required for use. Typically 3 x Volume Size`

#### ExistingSubnetGroup
- Default: ``
- Type: `String`
- Description: `The existing DB subnet group to use for this instance. (OPTIONAL)`

#### DomainIAMRoleManagedPolicyArns
- Default: ``
- Type: `String`
- Description: `A comma delimited list of IAM policy ARNs for the DomainIAMRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### MasterUserPassword
- ConstraintDescription: `Must be between 1 and 128 characters and cannot contain '@', '"', or '\/'.`
- Description: `Password for the local administrator account. Must be at least 8 characters containing letters, numbers and symbols.`
- MinLength: `8`
- AllowedPattern: `^[\p{ASCII}&&[^@\s\/"]]+$||^$`
- NoEcho: `True`
- MaxLength: `128`
- Type: `String`

#### S3BackupRoleManagedPolicyArns
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A comma delimited list of IAM policy ARNs for the S3BackupRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

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

#### Timezone
- Default: ``
- Type: `String`
- Description: `The time zone of the DB instance, which you can specify to match the time zone of your applications`
- AllowedValues: `['', 'Afghanistan Standard Time', 'Alaskan Standard Time', 'Arabian Standard Time', 'Atlantic Standard Time', 'AUS Central Standard Time', 'AUS Eastern Standard Time', 'Belarus Standard Time', 'Canada Central Standard Time', 'Cape Verde Standard Time', 'Cen. Australia Standard Time', 'Central America Standard Time', 'Central Asia Standard Time', 'Central Brazilian Standard Time', 'Central Europe Standard Time', 'Central European Standard Time', 'Central Pacific Standard Time', 'Central Standard Time', 'Central Standard Time (Mexico)', 'China Standard Time', 'E. Africa Standard Time', 'E. Australia Standard Time', 'E. Europe Standard Time', 'E. South America Standard Time', 'Eastern Standard Time', 'Georgian Standard Time', 'GMT Standard Time', 'Greenland Standard Time', 'Greenwich Standard Time', 'GTB Standard Time', 'Hawaiian Standard Time', 'India Standard Time', 'Jordan Standard Time', 'Korea Standard Time', 'Middle East Standard Time', 'Mountain Standard Time', 'Mountain Standard Time (Mexico)', 'New Zealand Standard Time', 'Newfoundland Standard Time', 'Pacific Standard Time', 'Pacific Standard Time (Mexico)', 'Russian Standard Time', 'SE Asia Standard Time', 'Singapore Standard Time', 'Tokyo Standard Time', 'US Eastern Standard Time', 'UTC', 'UTC-02', 'UTC-08', 'UTC-09', 'UTC-11', 'UTC+12', 'W. Australia Standard Time', 'W. Central Africa Standard Time', 'W. Europe Standard Time']`

#### DBInstanceClass
- Default: `db.m4.large`
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
- Default: `1433`
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
