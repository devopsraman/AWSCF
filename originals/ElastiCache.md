
## Description

Rackspace Hosting - AWS Memcached or Redis Cluster for ElastiCache

#### Metadata

 * **AWS::CloudFormation::Interface**: {u'ParameterGroups': [{u'Parameters': [u'Environment', u'VPCId', u'ElastiCacheSubnets', u'VPCSecurityGroupIds'], u'Label': {u'default': u'VPC Configuration'}}, {u'Parameters': [u'ElastiCacheEngineType', u'InstanceClass', u'NumberOfNodes', u'CacheClusterPort'], u'Label': {u'default': u'ElastiCache Basic Configuration'}}, {u'Parameters': [u'FailoverEnabled', u'InstanceClass', u'NumberOfNodes', u'CacheClusterPort', u'EnableNotifications', u'MinorVersionUpgrade'], u'Label': {u'default': u'ElastiCache Advanced Configuration'}}, {u'Parameters': [u'ReplicationGroupDescription'], u'Label': {u'default': u'Redis Specific'}}, {u'Parameters': [u'ClusterName'], u'Label': {u'default': u'Memcached Specific'}}, {u'Parameters': [u'SnapshotRetentionLimit', u'PreferredSnapshotWindow', u'PreferredMaintenanceWindow'], u'Label': {u'default': u'Backup / Maintenance'}}]}
 * **Version**: v1.0.1

## Parameters

 * **CacheClusterPort** - The number of cache nodes within the ElastiCache cluster
  * Default: `6379`
 * **ClusterName** - Name of Cluster
  * Default: `MyCluster`
 * **ElastiCacheEngineType** - The name of the cache engine to be used for this cache cluster
  * Default: `redis28`
 * **ElastiCacheSubnets** - Subnets for use with this cache cluster
 * **EnableNotifications** - Specifies whether to notify about ElastiCache Cluster Events.
  * Default: `False`
 * **Environment** - Application environment for which this Cache Cluster is being created. e.g. Development/Production
  * Default: `Development`
 * **FailoverEnabled** - Specifies if enable failover
  * Default: `True`
 * **InstanceClass** - The compute and memory capacity of the nodes within the ElastiCache cluster
  * Default: `cache.m3.medium`
 * **MinorVersionUpgrade** - Specifies version upgrade is enabled
  * Default: `True`
 * **NumberOfNodes** - The number of cache nodes within the ElastiCache cluster
  * Default: `1`
 * **PreferredMaintenanceWindow** - The daily time range during which automated backups are created if automated backups are enabled
  * Default: `Sun:05:00-Sun:07:00`
 * **PreferredSnapshotWindow** - The daily time range during which automated backups are created if automated backups are enabled
  * Default: `Sun:03:00-Sun:04:00`
 * **ReplicationGroupDescription** - Description of Replication Group (redis only)
  * Default: `Elasticache`
 * **SnapshotRetentionLimit** - The number of days for which automated backups are retained. Setting this parameter to a positive number enables backups. Setting this parameter to 0 disables automated backups.
  * Default: `7`
  * Constraint: `must be between 0 and 35`
 * **VPCId** - Existing Virtual Private Cloud to use with the elasticache cluster
 * **VPCSecurityGroupIds** - Existing security group being used by Elasticache.
  * Default: ``

## Conditions

 * **AutoFailover** - `{u'Fn::Equals': [{u'Ref': u'FailoverEnabled'}, u'True']}`
 * **Memcached** - `{u'Fn::Equals': [{u'Ref': u'ElastiCacheEngineType'}, u'memcached14']}`
 * **NotificationsEnabled** - `{u'Fn::Equals': [{u'Ref': u'EnableNotifications'}, u'True']}`
 * **Redis** - `{u'Fn::Equals': [{u'Ref': u'ElastiCacheEngineType'}, u'redis28']}`

## Mappings

 * **ElastiCacheEngine**:
  * `(u'redis28', {u'Version': u'2.8.24', u'ParameterGroupName': u'default.redis2.8', u'Name': u'redis'})`
  * `(u'memcached14', {u'Version': u'1.4.24', u'ParameterGroupName': u'default.memcached1.4', u'Name': u'memcached'})`

## Resources

 * **CacheCluster** - `AWS::ElastiCache::CacheCluster`
 * **ElastiCacheRepGroup** - `AWS::ElastiCache::ReplicationGroup`
 * **ElastiCacheSubnetGroup** - `AWS::ElastiCache::SubnetGroup`

## Outputs

 * **MemcachedConnection** - `{u'Fn::Join': [u':', [{u'Fn::GetAtt': [u'CacheCluster', u'ConfigurationEndpoint.Address']}, {u'Fn::GetAtt': [u'CacheCluster', u'ConfigurationEndpoint.Port']}]]}`
 * **RedisConnection** - `{u'Fn::Join': [u':', [{u'Fn::GetAtt': [u'ElastiCacheRepGroup', u'PrimaryEndPoint.Address']}, {u'Fn::GetAtt': [u'ElastiCacheRepGroup', u'PrimaryEndPoint.Port']}]]}`