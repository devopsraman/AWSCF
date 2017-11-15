Redshift FAWS Template
======================
redshift.template - AWS Redshift
### Parameters

#### InternalRecordName
- Default: ``
- Type: `String`
- Description: `Record Name for the new Resource Record in the Internal Hosted Zone`

#### PubliclyAccessible
- Default: `False`
- ConstraintDescription: `Must be either True or False`
- Type: `String`
- Description: `Indicates whether the Redshift cluster is an Internet-facing cluster`
- AllowedValues: `['True', 'False']`

#### MasterUsername
- AllowedPattern: `^[^\d][a-zA-Z0-9_]+?$`
- Type: `String`
- Description: `The name of master user for the Redshift instance`
- MaxLength: `64`

#### RedshiftInstanceClass
- Default: `dc1.large`
- Type: `String`
- Description: `The compute and memory capacity of the nodes within the Redshift cluster`
- AllowedValues: `['dc1.large', 'dc1.8xlarge', 'ds2.xlarge', 'ds2.8xlarge']`

#### RedshiftSubnets
- Type: `List<AWS::EC2::Subnet::Id>`
- Description: `Subnets for use with this Redshift cluster`

#### VPCSecurityGroupIds
- Default: ``
- Type: `List<AWS::EC2::SecurityGroup::Id>`
- Description: `Existing security group being used by Redshift`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### MasterUserPasswords
- AllowedPattern: `^[\p{ASCII}&&[^@\s\/"]]+$||^$`
- MinLength: `8`
- Type: `String`
- NoEcho: `True`
- MaxLength: `64`

#### CWPercentageDiskUsed
- Default: `90`
- Type: `Number`
- Description: `CloudWatch Percentage of storage consumed threshold`

#### EnableRackspaceTicket
- Default: `False`
- Type: `String`
- Description: `Specifies whether alarms will generate Rackspace tickets`
- AllowedValues: `['False', 'True']`

#### NumberOfNodes
- Default: `1`
- MinValue: `1`
- Type: `Number`
- Description: `If ClusterType is single-node, this parameter is ignored. If ClusterType is multi-node, NumberOfNodes must be >= 2.`
- MaxValue: `100`

#### KeyId
- Default: ``
- Type: `String`
- Description: `The ID of the AWS Key Management Service (AWS KMS) key that you want to use to encrypt data in the cluster`

#### ClusterVersion
- Default: `1.0`
- Type: `String`
- Description: `Redshift Engine Version`
- AllowedValues: `['1.0']`

#### InternalZoneName
- Default: ``
- Type: `String`
- Description: `TLD for Internal Hosted Zone`

#### ClusterRoleManagedPolicyArns
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A comma delimited list of IAM policy ARNs for the ClusterRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### BackupRetentionPeriod
- Description: `The number of days for which automated backups are retained. Setting this parameter to a positive number enables backups. Setting this parameter to 0 disables automated backups`
- Default: `1`
- Type: `Number`
- MaxValue: `35`
- MinValue: `0`
- ConstraintDescription: `must be between 0 and 35`

#### DBName
- Default: `myredshift`
- AllowedPattern: `^(?=.{1,63}$)[a-z][a-z0-9_]*`
- Type: `String`
- Description: `Name of initial Redshift database`
- ConstraintDescription: `Must be lower-case, begin with a letter, contain alphanumeric characters or underscores, and have a maximum length of 63`

#### PreferredMaintenanceWindow
- Default: `Sun:05:00-Sun:07:00`
- Type: `String`
- Description: `The daily time range during which automated backups are created if automated backups are enabled`

#### ElasticIP
- Default: ``
- Type: `String`
- Description: `The Elastic IP (EIP) address for the cluster (must have publicly accessible enabled)`

#### CWCPUThreshold
- Default: `90`
- Type: `Number`
- Description: `CloudWatch CPUUtilization Threshold`

#### ClusterType
- Default: `single-node`
- Type: `String`
- Description: `Create a single-node or multi-node Redshift cluster`
- AllowedValues: `['single-node', 'multi-node']`

#### AllowVersionUpgrade
- Default: `True`
- Type: `String`
- Description: `Indicates that engine upgrades will be applied automatically to the Redshift cluster during the maintenance window`
- AllowedValues: `['True', 'False']`

#### RedshiftSnapshotIdentifier
- Default: ``
- Type: `String`
- Description: `The name of the snapshot from which to create a new cluster (optional)`

#### AvailabilityZone
- Default: ``
- Type: `String`
- Description: `Availability zone in which to initially provision Redshift. OPTIONAL`

#### StorageEncrypted
- Default: `False`
- Type: `String`
- ConstraintDescription: `Must be either True or False`
- Description: `Specifies whether the Redshift cluster is encrypted`
- AllowedValues: `['True', 'False']`

#### InternalZoneId
- Default: ``
- Type: `String`
- Description: `The Route53 Internal Hosted Zone ID`

#### Port
- Description: `The port number on which the database accepts connections`
- Default: `5439`
- ConstraintDescription: `Must be between 1150 and 65535.`
- MaxValue: `65535`
- MinValue: `1150`
- Type: `Number`

### Outputs
- `JDBCConnectionString`
- `DBPort`
- `RedshiftClusterIdentifier`
- `RedshiftAddress`

### Alarms
#### CPUAlarmHigh
- Description: `{'Fn::Sub': 'Alarm if ${RedshiftCluster} CPU > ${CWCPUThreshold}% for 5 minutes'}`
- Metric: CPUUtilization
- Threshold: `{'Ref': 'CWCPUThreshold'}`
- Actions: []

#### ClusterHealthTicket
- Description: Cluster has entered unhealthy state, creating ticket
- Metric: HealthStatus
- Threshold: 1
- Actions: `{'Fn::If': ['RackspaceAlarmsEnabled', {'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-emergency'}, {'Ref': 'AWS::NoValue'}]}`

#### FreeStorageSpaceTicket
- Description: Consumed storage space has risen above threshold, sending email notification
- Metric: PercentageDiskSpaceUsed
- Threshold: `{'Ref': 'CWPercentageDiskUsed'}`
- Actions: `{'Fn::If': ['RackspaceAlarmsEnabled', {'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-urgent'}, {'Ref': 'AWS::NoValue'}]}`
