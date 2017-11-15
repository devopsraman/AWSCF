RdsMysqlReplica FAWS Template
=============================
rds_mysql_replica.template - Creates the necessary resources for an RDS instance. Please be aware that this template will create resources for which you will be charged.
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

#### EnableRackspaceTicket
- Default: `False`
- Type: `String`
- Description: `Specifies whether alarms will generate Rackspace tickets`
- AllowedValues: `['False', 'True']`

#### Engine
- Default: `mysql`
- Type: `String`
- Description: `Database Engine Type.`
- AllowedValues: `['mysql']`

#### CrossRegionReplica
- Default: `False`
- ConstraintDescription: `Must be either True or False.`
- Type: `String`
- Description: `Specifies whether the Read Replica is in another region as the Master.`
- AllowedValues: `['True', 'False']`

#### EventCategories
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A list of RDS event categories.  Submissions will be made to the provided NotificationTopic for each matching event. Acceptable values can be found with the CLI command 'aws rds describe-event-categories' (OPTIONAL)`

#### MajorEngineVersion
- Default: `5.7`
- Type: `String`
- Description: `Database Engine Major Version`
- AllowedValues: `[u'5.5', u'5.6', u'5.7']`

#### MinorEngineVersion
- Default: `5.7.19`
- Type: `String`
- Description: `Database Engine Minor Version http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_CreateDBInstance.html`
- AllowedValues: `[u'5.6.37', u'5.6.27', u'5.6.35', u'5.6.29', u'5.6.34', u'5.5.46', u'5.5.54', u'5.5.57', u'5.7.17', u'5.7.16', u'5.5.53', u'5.7.19']`

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
- Default: `mysql5.7`
- Type: `String`
- Description: `Parameter Group Family Name (ex. mysql5.7,sqlserver-se-12.0,postgres9.5,oracle-se-12.1,mariadb10.1)`
- AllowedValues: `[u'mysql5.5', u'mysql5.7', u'mysql5.6']`

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

#### PreferredMaintenanceWindow
- Default: `Sun:07:00-Sun:08:00`
- AllowedPattern: `^(Mon|Tue|Wed|Thu|Fri|Sat|Sun):[0-9]{2}:[0-9]{2}-(Mon|Tue|Wed|Thu|Fri|Sat|Sun):[0-9]{2}:[0-9]{2}$`
- Type: `String`
- Description: `The daily time range during which automated backups are created if automated backups are enabled.`
- ConstraintDescription: `Must be in the format ddd:hh24:mi-ddd:hh24:mi`

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

#### SourceDBInstance
- Default: ``
- Type: `String`
- Description: `The ID of the source DB instance. For a source instance in another region, use the full ARN (optional).  Cannot be used with DBSnapshotName parameter.`

#### ExistingSubnetGroup
- Default: ``
- Type: `String`
- Description: `The existing DB subnet group to use for this instance. (OPTIONAL)`

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
- Default: `3306`
- Type: `Number`
- MaxValue: `65535`
- MinValue: `1150`
- ConstraintDescription: `Must be between 1150 and 65535.`

#### DBInstanceIdentifier
- Default: ``
- Type: `String`
- Description: `The DB instance identifier. This parameter is stored as a lowercase string. (optional)`

### Outputs
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

#### ReplicaLag
- Description: ReplicaLag has exceeded threshold, generating ticket.
- Metric: ReplicaLag
- Threshold: 3600
- Actions: ["`{'Fn::If': ['RackspaceAlarmsEnabled', {'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-urgent'}, {'Ref': 'AWS::NoValue'}]}`", "`{'Fn::If': ['isNotification', {'Ref': 'NotificationTopic'}, {'Ref': 'AWS::NoValue'}]}`"]
