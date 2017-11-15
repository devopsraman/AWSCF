
## Description

Rackspace Hosting - Creates the necessary resources for an Aurora Cluster. Please be aware that this template will create resources for which you will be charged.

#### Metadata

 * **AWS::CloudFormation::Interface**: {u'ParameterGroups': [{u'Parameters': [u'VPCID', u'RDSSubnets', u'VPCSecurityGroupIds'], u'Label': {u'default': u'VPC Configuration'}}, {u'Parameters': [u'Engine', u'DBInstanceClass', u'DBInstanceIdentifier', u'DBName', u'MasterUsername', u'MasterUserPassword', u'StorageEncrypted', u'DBSnapshotName', u'MultiAZ', u'PubliclyAccessible', u'Port'], u'Label': {u'default': u'RDS Configuration'}}, {u'Parameters': [u'AutoMinorVersionUpgrade', u'BackupRetentionPeriod', u'PreferredBackupWindow', u'PreferredMaintenanceWindow', u'NotificationEmail'], u'Label': {u'default': u'Backups'}}]}

## Parameters

 * **AutoMinorVersionUpgrade** - Indicates that minor engine upgrades will be applied automatically to the DB instance during the maintenance window.
  * Default: `True`
  * Constraint: `Must be either True or False.`
 * **BackupRetentionPeriod** - The number of days for which automated backups are retained. Setting this parameter to a positive number enables backups. Setting this parameter to 0 disables automated backups.
  * Default: `1`
  * Constraint: `Must be between 0 and 35`
 * **DBInstanceClass** - The database instance type
  * Default: `db.r3.large`
  * Constraint: `Must select a valid database instance type.`
 * **DBInstanceIdentifier** - The DB instance identifier. This parameter is stored as a lowercase string.
  * Default: `Aurora`
 * **DBSnapshotName** - The name of a DB snapshot (optional)
  * Default: ``
 * **Environment** - Application environment for which this RDS is being created. e.g. Development/Production
  * Default: `Development`
 * **MasterUserPassword** - Password for the local administrator account. Must be at least 8 characters containing letters, numbers and symbols.
 * **MasterUsername** - The name of master user for the client DB instance.
 * **NotificationEmail** - SNS topic to notify if there are operational issues
  * Constraint: `Must be a valid email address.`
 * **Port** - The port number on which the database accepts connections.
  * Default: `3306`
  * Constraint: `Must be between 1150 and 65535`
 * **PreferredBackupWindow** - The daily time range during which automated backups are created if automated backups are enabled.
  * Default: `05:00-06:00`
 * **PreferredMaintenanceWindow** - The daily time range during which automated backups are created if automated backups are enabled.
  * Default: `Sun:07:00-Sun:08:00`
 * **PubliclyAccessible** - Indicates whether the database instance is an Internet-facing instance.
  * Default: `False`
  * Constraint: `Must be either True or False.`
 * **RDSSubnets** - Subnets for RDS Instances
 * **StorageEncrypted** - Specifies whether the DB instance is encrypted.
  * Default: `False`
  * Constraint: `Must be either True or False.`
 * **VPCID** - Select Virtual Private Cloud ID
 * **VPCSecurityGroupIds** - Existing security groups being used by App ec2 instances. If no AppSG, enter the VPC Default.
  * Default: ``

## Conditions

 * **UseDBSnapshot** - `{u'Fn::Not': [{u'Fn::Equals': [{u'Ref': u'DBSnapshotName'}, u'']}]}`

## Mappings

 * **InstanceTypeMap**:
  * `(u'db.r3.xlarge', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.r3.2xlarge', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.r3.8xlarge', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.r3.large', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.r3.4xlarge', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`

## Resources

 * **CPUAlarmHigh01** - `AWS::CloudWatch::Alarm`
 * **CPUAlarmHigh02** - `AWS::CloudWatch::Alarm`
 * **ClusterParameterGroup** - `AWS::RDS::DBClusterParameterGroup`
 * **DBSubnetGroup** - `AWS::RDS::DBSubnetGroup`
 * **NotificationTopic** - `AWS::SNS::Topic`
 * **OptionGroup** - `AWS::RDS::OptionGroup`
 * **ParameterGroup** - `AWS::RDS::DBParameterGroup`
 * **RDSCluster** - `AWS::RDS::DBCluster`
 * **RDSInstance01** - `AWS::RDS::DBInstance`
 * **RDSInstance02** - `AWS::RDS::DBInstance`
 * **ReadIOPSHigh01** - `AWS::CloudWatch::Alarm`
 * **ReadIOPSHigh02** - `AWS::CloudWatch::Alarm`
 * **WriteIOPSHigh01** - `AWS::CloudWatch::Alarm`
 * **WriteIOPSHigh02** - `AWS::CloudWatch::Alarm`

## Outputs

 * **ClusterAddress** - `{u'Fn::GetAtt': [u'RDSCluster', u'Endpoint.Address']}`
 * **DBPort** - `{u'Fn::GetAtt': [u'RDSCluster', u'Endpoint.Port']}`