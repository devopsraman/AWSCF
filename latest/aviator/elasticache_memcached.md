ElasticacheMemcached FAWS Template
==================================
elasticache_memcached.template - AWS Cluster for ElastiCache
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

#### ClusterName
- Default: `MyMemcachedCluster`
- Type: `String`
- Description: `Name of Cluster`

#### VPCSecurityGroupIds
- Default: ``
- Type: `List<AWS::EC2::SecurityGroup::Id>`
- Description: `Existing security group being used by Elasticache cluster.`

#### CacheClusterPort
- Default: `11211`
- MinValue: `1024`
- Type: `Number`
- Description: `The port number on which each of the cache nodes will accept connections`
- MaxValue: `65535`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### InstanceClass
- Default: `cache.m3.medium`
- Type: `String`
- Description: `The compute and memory capacity of the nodes within the ElastiCache cluster`
- AllowedValues: `['cache.t2.micro', 'cache.t2.small', 'cache.t2.medium', 'cache.c1.xlarge', 'cache.m3.medium', 'cache.m3.large', 'cache.m3.xlarge', 'cache.m3.2xlarge', 'cache.m4.large', 'cache.m4.xlarge', 'cache.m4.2xlarge', 'cache.m4.4xlarge', 'cache.m4.10xlarge', 'cache.r3.large', 'cache.r3.xlarge', 'cache.r3.2xlarge', 'cache.r3.4xlarge', 'cache.r3.8xlarge']`

#### ElastiCacheEngineType
- Default: `memcached14`
- Type: `String`
- Description: `The name of the cache engine to be used for this memcached cache cluster`
- AllowedValues: `['memcached14']`

#### NumberOfNodes
- Default: `1`
- MinValue: `1`
- Type: `Number`
- Description: `The number of cache nodes within the ElastiCache cluster`
- MaxValue: `100`

#### InternalZoneId
- Default: ``
- Type: `String`
- Description: `The Route53 Internal Hosted Zone ID`

#### PreferredMaintenanceWindow
- Default: `Sun:05:00-Sun:07:00`
- Type: `String`
- Description: `The weekly time range (in UTC) during which system maintenance can occur.`

### Outputs
- `MemcachedConnection`

### Alarms