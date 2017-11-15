Elasticsearch FAWS Template
===========================
elasticsearch.template - Elasticsearch domain template.
### Parameters

#### MasterNodeInstanceType
- Default: `m3.large.elasticsearch`
- ConstraintDescription: `Must be a valid Elasticsearch instance type`
- Type: `String`
- Description: `Select master instance type`
- AllowedValues: `['t2.micro.elasticsearch', 't2.small.elasticsearch', 't2.medium.elasticsearch', 'm3.medium.elasticsearch', 'm3.large.elasticsearch', 'm3.xlarge.elasticsearch', 'm3.2xlarge.elasticsearch', 'm4.large.elasticsearch', 'm4.xlarge.elasticsearch', 'm4.2xlarge.elasticsearch', 'm4.4xlarge.elasticsearch', 'm4.10xlarge.elasticsearch', 'c4.large.elasticsearch', 'c4.xlarge.elasticsearch', 'c4.2xlarge.elasticsearch', 'c4.4xlarge.elasticsearch', 'c4.8xlarge.elasticsearch', 'r3.large.elasticsearch', 'r3.xlarge.elasticsearch', 'r3.2xlarge.elasticsearch', 'r3.4xlarge.elasticsearch', 'r3.8xlarge.elasticsearch', 'r4.large.elasticsearch', 'r4.xlarge.elasticsearch', 'r4.2xlarge.elasticsearch', 'r4.4xlarge.elasticsearch', 'r4.8xlarge.elasticsearch', 'r4.16xlarge.elasticsearch', 'i2.xlarge.elasticsearch', 'i2.2xlarge.elasticsearch']`

#### InternalZoneName
- Default: ``
- Type: `String`
- Description: `TLD for Internal Hosted Zone`

#### ESVersion
- Default: `5.1`
- Type: `String`
- Description: `ElasticSearch Version.`
- AllowedValues: `['1.5', '2.3', '5.1']`

#### EbsVolumeSize
- Default: `20`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `The size of the EBS volume for each data node.`
- ConstraintDescription: `Must be a valid integer.`

#### MasterNodeCount
- Default: `3`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `Number of master (non-data) nodes in the cluster.`
- ConstraintDescription: `Must be a valid integer <= 20.`

#### ESDomainName
- Type: `String`
- Description: `AWS Elasticsearch name for domain`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### IPAddressWhiteList
- Type: `CommaDelimitedList`
- Description: `IP Addresses allowed to access the ElasticSearch Cluster`

#### InternalRecordName
- Default: ``
- Type: `String`
- Description: `Record Name for the new Resource Record in the Internal Hosted Zone`

#### DataNodeCount
- Default: `6`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `Number of Data Nodes in the Elasticsearch cluster.`
- ConstraintDescription: `Must be a valid, even integer.`

#### AutomatedSnapshotStartHour
- AllowedPattern: `([0-9]+)`
- Default: `0`
- Type: `String`
- Description: `The hour (0-23) to issue a daily snapshot of Elasticsearch cluster.`
- ConstraintDescription: `Must be a valid integer between 0 - 23.`

#### EbsVolumeType
- Default: `gp2`
- Type: `String`
- Description: `The EBS volume type to use with the Amazon ES domain, such as standard, gp2, or io1.`
- AllowedValues: `['io1', 'standard', 'gp2']`

#### DataNodeInstanceType
- Default: `m3.large.elasticsearch`
- ConstraintDescription: `Must be a valid Elasticsearch instance type`
- Type: `String`
- Description: `Select data node instance type`
- AllowedValues: `['t2.micro.elasticsearch', 't2.small.elasticsearch', 't2.medium.elasticsearch', 'm3.medium.elasticsearch', 'm3.large.elasticsearch', 'm3.xlarge.elasticsearch', 'm3.2xlarge.elasticsearch', 'm4.large.elasticsearch', 'm4.xlarge.elasticsearch', 'm4.2xlarge.elasticsearch', 'm4.4xlarge.elasticsearch', 'm4.10xlarge.elasticsearch', 'c4.large.elasticsearch', 'c4.xlarge.elasticsearch', 'c4.2xlarge.elasticsearch', 'c4.4xlarge.elasticsearch', 'c4.8xlarge.elasticsearch', 'r3.large.elasticsearch', 'r3.xlarge.elasticsearch', 'r3.2xlarge.elasticsearch', 'r3.4xlarge.elasticsearch', 'r3.8xlarge.elasticsearch', 'r4.large.elasticsearch', 'r4.xlarge.elasticsearch', 'r4.2xlarge.elasticsearch', 'r4.4xlarge.elasticsearch', 'r4.8xlarge.elasticsearch', 'r4.16xlarge.elasticsearch', 'i2.xlarge.elasticsearch', 'i2.2xlarge.elasticsearch']`

#### EbsIops
- Default: `0`
- AllowedPattern: `([0-9]+)`
- Type: `String`
- Description: `The number of I/O operations per second (IOPS) that the volume supports.`
- ConstraintDescription: `Must be a valid integer.`

#### InternalZoneId
- Default: ``
- Type: `String`
- Description: `The Route53 Internal Hosted Zone ID`

### Outputs

### Alarms