ElasticacheRedisMultiShard FAWS Template
========================================
elasticache_redis_multi_shard.template - AWS Cluster for ElastiCache
### Parameters

#### InternalZoneName
- Default: ``
- Type: `String`
- Description: `TLD for Internal Hosted Zone`

#### InternalRecordName
- Default: ``
- Type: `String`
- Description: `Record Name for the new Resource Record in the Internal Hosted Zone`

#### ElastiCacheSubnets
- Type: `List<AWS::EC2::Subnet::Id>`
- Description: `Subnets for use with this cache cluster`

#### SnapshotRetentionLimit
- Description: `The number of days for which automated backups are retained. Setting this parameter to a positive number enables backups. Setting this parameter to 0 disables automated backups.`
- Default: `7`
- Type: `Number`
- MaxValue: `35`
- MinValue: `0`
- ConstraintDescription: `must be between 0 and 35`

#### ClusterName
- Default: `MyRedisCluster`
- AllowedPattern: `^[a-zA-Z][a-zA-Z0-9\-]{0,19}$`
- Type: `String`
- Description: `Name of Cluster`
- ConstraintDescription: `Must be between 1 and 20 alphanumeric characters and begin with a letter.`

#### ReplicationGroupDescription
- Default: `Elasticache`
- Type: `String`
- Description: `Description of Replication Group`

#### VPCSecurityGroupIds
- Default: ``
- Type: `List<AWS::EC2::SecurityGroup::Id>`
- Description: `Existing security group being used by Elasticache cluster.`

#### CacheClusterPort
- Default: `6379`
- MinValue: `1024`
- Type: `Number`
- Description: `The port number on which each of the cache nodes will accept connections`
- MaxValue: `65535`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### NumberOfShards
- Default: `2`
- MinValue: `2`
- Type: `Number`
- Description: `Number of shards`
- MaxValue: `15`

#### InstanceClass
- Default: `cache.m3.medium`
- Type: `String`
- Description: `The compute and memory capacity of the nodes within the ElastiCache cluster`
- AllowedValues: `['cache.t2.micro', 'cache.t2.small', 'cache.t2.medium', 'cache.c1.xlarge', 'cache.m3.medium', 'cache.m3.large', 'cache.m3.xlarge', 'cache.m3.2xlarge', 'cache.m4.large', 'cache.m4.xlarge', 'cache.m4.2xlarge', 'cache.m4.4xlarge', 'cache.m4.10xlarge', 'cache.r3.large', 'cache.r3.xlarge', 'cache.r3.2xlarge', 'cache.r3.4xlarge', 'cache.r3.8xlarge']`

#### ElastiCacheEngineType
- Default: `redis32`
- Type: `String`
- Description: `The redis engine version`
- AllowedValues: `['redis32']`

#### SnapshotWindow
- Default: `03:00-05:00`
- Type: `String`
- Description: `The daily time range (in UTC) during which ElastiCache will begin taking a daily snapshot of your node group.`

#### NotificationTopic
- Default: ``
- Type: `String`
- Description: `SNS Topic ARN to notify if there are any ElastiCache notifications. OPTIONAL`

#### NumberOfReadReplicasPerShard
- Default: `2`
- MinValue: `2`
- Type: `Number`
- Description: `Number of read replicas per shard`
- MaxValue: `5`

#### InternalZoneId
- Default: ``
- Type: `String`
- Description: `The Route53 Internal Hosted Zone ID`

#### PreferredMaintenanceWindow
- Default: `Sun:05:00-Sun:07:00`
- Type: `String`
- Description: `The weekly time range (in UTC) during which system maintenance can occur.`

### Outputs
- `RedisConnection`

### Alarms