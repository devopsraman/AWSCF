
## Description

Rackspace Hosting - Creates the necessary resources for an RDS instance. Please be aware that this template will create resources for which you will be charged.

#### Metadata

 * **AWS::CloudFormation::Interface**: {u'ParameterGroups': [{u'Parameters': [u'Environment', u'VPCID', u'RDSSubnets', u'VPCSecurityGroupIds'], u'Label': {u'default': u'VPC Configuration'}}, {u'Parameters': [u'Engine', u'MinorEngineVersion', u'MajorEngineVersion', u'DBInstanceIdentifier', u'DBInstanceClass', u'RDSVolumeSize', u'RDSVolumeType', u'DBName', u'Port'], u'Label': {u'default': u'RDS Basic Configuration'}}, {u'Parameters': [u'MultiAZ', u'AutoMinorVersionUpgrade', u'ParameterGroupFamily', u'StorageEncrypted', u'PubliclyAccessible'], u'Label': {u'default': u'RDS Advanced Configuration'}}, {u'Parameters': [u'MasterUsername', u'MasterUserPassword'], u'Label': {u'default': u'RDS User/DB/Pass Configuration'}}, {u'Parameters': [u'PreferredBackupWindow', u'PreferredMaintenanceWindow', u'BackupRetentionPeriod', u'DBSnapshotName'], u'Label': {u'default': u'Backup / Maintenance'}}]}
 * **Version**: v0.2.0

## Parameters

 * **AutoMinorVersionUpgrade** - Indicates that minor engine upgrades will be applied automatically to the DB instance during the maintenance window.
  * Default: `True`
  * Constraint: `Must be either True or False.`
 * **BackupRetentionPeriod** - The number of days for which automated backups are retained. Setting this parameter to a positive number enables backups. Setting this parameter to 0 disables automated backups.
  * Default: `1`
  * Constraint: `Must be between 0 and 35.`
 * **DBInstanceClass** - The database instance type.
  * Default: `db.t2.medium`
  * Constraint: `Must select a valid database instance type.`
 * **DBInstanceIdentifier** - The DB instance identifier. This parameter is stored as a lowercase string. (optional)
  * Default: ``
 * **DBName** - The meaning of this parameter differs according to the database engine you use.
  * Default: `MyRDS`
 * **DBSnapshotName** - The name of a DB snapshot (optional).
  * Default: ``
 * **Engine** - Database Engine Type.
  * Default: `MySQL`
 * **Environment** - Application environment for which this RDS is being created. e.g. Development/Production
  * Default: `Development`
 * **MajorEngineVersion** - Database Engine Major Version (ex. 5.7,12.00,9.5,12.1,10.1)
 * **MasterUserPassword** - Password for the local administrator account. Must be at least 8 characters containing letters, numbers and symbols.
  * Default: `ChangeMe123!`
 * **MasterUsername** - The name of master user for the client DB instance.
  * Default: `MyUser`
 * **MinorEngineVersion** - Database Engine Minor Version http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_CreateDBInstance.html
 * **MultiAZ** - Create a multi-AZ RDS database instance
  * Default: `True`
  * Constraint: `Must be either True or False.`
 * **NotificationEmail** - EMail address to notify if there are any alarms.
  * Constraint: `Must be a valid email address.`
 * **ParameterGroupFamily** - Parameter Group Family Name (ex. mysql5.7,sqlserver-se-12.0,postgres9.5,oracle-se-12.1,mariadb10.1)
 * **Port** - The port number on which the database accepts connections.
  * Default: `3306`
  * Constraint: `Must be between 1150 and 65535.`
 * **PreferredBackupWindow** - The daily time range during which automated backups are created if automated backups are enabled.
  * Default: `05:00-06:00`
 * **PreferredMaintenanceWindow** - The daily time range during which automated backups are created if automated backups are enabled.
  * Default: `Sun:07:00-Sun:08:00`
 * **PubliclyAccessible** - Indicates whether the database instance is an Internet-facing instance.
  * Default: `False`
  * Constraint: `Must be either True or False.`
 * **RDSSubnets** - Subnets for RDS Instances
 * **RDSVolumeSize** - Select RDS Volume Size in GB.
  * Default: `10`
 * **RDSVolumeType** - Select RDS Volume Type.
  * Default: `gp2`
 * **StorageEncrypted** - Specifies whether the DB instance is encrypted.
  * Default: `False`
  * Constraint: `Must be either True or False.`
 * **VPCID** - Select Virtual Private Cloud ID.
 * **VPCSecurityGroupIds** - Existing security groups being used by App ec2 instances. If no AppSG, enter the VPC Default.
  * Default: ``

## Conditions

 * **IopsEnabled** - `{u'Fn::Equals': [{u'Ref': u'RDSVolumeType'}, u'io1']}`
 * **UseDBIdentifier** - `{u'Fn::Not': [{u'Fn::Equals': [{u'Ref': u'DBInstanceIdentifier'}, u'']}]}`
 * **UseDBSnapshot** - `{u'Fn::Not': [{u'Fn::Equals': [{u'Ref': u'DBSnapshotName'}, u'']}]}`
 * **UseMirroring** - `{u'Fn::Equals': [{u'Ref': u'MultiAZ'}, u'Mirror']}`

## Mappings

 * **InstanceTypeMap**:
  * `(u'db.r3.xlarge', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.m4.4xlarge', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.m4.large', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.m4.2xlarge', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.t2.medium', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.m3.xlarge', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.m3.large', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.m4.xlarge', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.r3.4xlarge', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.m3.medium', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.m4.10xlarge', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.r3.large', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.t2.small', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.r3.2xlarge', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.m3.2xlarge', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.r3.8xlarge', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.t2.large', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
  * `(u'db.t2.micro', {u'WriteIOPSLimit': u'100', u'CPULimit': u'60', u'FreeStorageSpaceLimit': u'1024', u'ReadIOPSLimit': u'100'})`
 * **RDSStorage**:
  * `(u'gp2', {u'10': u'100', u'20': u'100', u'200': u'600', u'30': u'100', u'50': u'150', u'40': u'120', u'100': u'300', u'500': u'1500'})`
  * `(u'io1', {u'10': u'300', u'20': u'600', u'200': u'6000', u'30': u'900', u'50': u'1500', u'40': u'1200', u'100': u'3000', u'500': u'15000'})`
  * `(u'standard', {u'10': u'100', u'20': u'100', u'200': u'100', u'30': u'100', u'50': u'100', u'40': u'100', u'100': u'100', u'500': u'100'})`

## Resources

 * **CPUAlarmHigh** - `AWS::CloudWatch::Alarm`
 * **DBSubnetGroup** - `AWS::RDS::DBSubnetGroup`
 * **FreeStorageSpaceEmail** - `AWS::CloudWatch::Alarm`
 * **FreeStorageSpaceTicket** - `AWS::CloudWatch::Alarm`
 * **NotificationTopic** - `AWS::SNS::Topic`
 * **RDSInstance** - `AWS::RDS::DBInstance`
 * **RDSOptionGroup** - `AWS::RDS::OptionGroup`
 * **RDSParameterGroup** - `AWS::RDS::DBParameterGroup`
 * **ReadIOPSHigh** - `AWS::CloudWatch::Alarm`
 * **WriteIOPSHigh** - `AWS::CloudWatch::Alarm`

## Outputs

 * **DBAddress** - `{u'Fn::Join': [u'', [{u'Fn::GetAtt': [u'RDSInstance', u'Endpoint.Address']}]]}`
 * **DBPort** - `{u'Fn::Join': [u'', [{u'Fn::GetAtt': [u'RDSInstance', u'Endpoint.Address']}]]}`
 * **JDBCConnectionString** - `{u'Fn::Join': [u'', [u'jdbc:mysql://', {u'Fn::GetAtt': [u'RDSInstance', u'Endpoint.Address']}, u':', {u'Fn::GetAtt': [u'RDSInstance', u'Endpoint.Port']}, u'/', {u'Ref': u'DBName'}]]}`
 * **RDSEndpoint** - `{u'Fn::Join': [u'', [{u'Fn::GetAtt': [u'RDSInstance', u'Endpoint.Address']}]]}`