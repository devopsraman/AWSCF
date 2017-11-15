Clb FAWS Template
=================
CLB.template - Elastic Load Balancer version 1 (Classic) Template.
### Parameters

#### InternalRecordName
- Default: ``
- Type: `String`
- Description: `Record Name for the new Resource Record in the Internal Hosted Zone`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### LoadBalancerPort1
- Default: `80`
- Type: `String`
- Description: `Specifies the external load balancer port number.`

#### ConnectionDrainingTimeout
- Default: `0`
- MinValue: `0`
- Type: `Number`
- Description: `Set the timeout value for elastic loadbalancer draining policy if desired. OPTIONAL`
- MaxValue: `3600`

#### LoadBalancerProtocol2
- Default: `HTTPS`
- Type: `String`
- Description: `Specifies the protocol to use for the Load Balancer HTTP / HTTPS / TCP / SSL.`
- AllowedValues: `['HTTP', 'HTTPS', 'TCP', 'SSL']`

#### LoadBalancerProtocol1
- Default: `HTTP`
- Type: `String`
- Description: `Specifies the protocol to use for the Load Balancer HTTP / HTTPS / TCP / SSL.`
- AllowedValues: `['HTTP', 'HTTPS', 'TCP', 'SSL']`

#### Scheme
- Default: `internet-facing`
- Type: `String`
- Description: `Specifies whether to create an internal CLB or a public facing one.`
- AllowedValues: `['internet-facing', 'internal']`

#### Subnets
- Type: `List<AWS::EC2::Subnet::Id>`
- Description: `A list of subnet IDs in your virtual private cloud (VPC) to attach to your load balancer.`

#### EnableRackspaceTicket
- Default: `False`
- Type: `String`
- Description: `Specifies whether alarms will generate Rackspace tickets`
- AllowedValues: `['False', 'True']`

#### HealthTimeout
- Default: `5`
- Type: `String`
- Description: `Number of seconds during which no response means a failed health probe.`

#### EnableListener1
- Default: `True`
- Type: `String`
- Description: `Enable Primary Listener on the Load Balancer`
- AllowedValues: `['True', 'False']`

#### CreateLoggingBucket
- Default: `true`
- Type: `String`
- Description: `Create a new S3 logging bucket`
- AllowedValues: `['true', 'false']`

#### AppCookieName
- Default: ``
- Type: `String`
- Description: `Generates a stickiness policy based upon an application cookie. Leave blank not to use.  Overrides CookieExpirationPeriod.`

#### InternalZoneName
- Default: ``
- Type: `String`
- Description: `TLD for Internal Hosted Zone`

#### SecurityGroups
- Type: `List<AWS::EC2::SecurityGroup::Id>`
- Description: `A list of security groups assigned to your load balancer within your virtual private cloud (VPC).`

#### InstancePort1
- Default: `80`
- Type: `String`
- Description: `Specifies the TCP port on which the instance server is listening.`

#### InstancePort2
- Default: `80`
- Type: `String`
- Description: `Specifies the TCP port on which the instance server is listening.`

#### HealthInterval
- Default: `30`
- Type: `String`
- Description: `Seconds between health checks.`

#### HealthTarget
- Default: `HTTP:80/`
- Type: `String`
- Description: `Protocol & port check on instance. TCP:5000 | SSL:5000 || HTTP(S) = HTTP:80/path/to/my/file.`

#### S3BucketPrefix
- Default: `FrontendCLBLogs`
- Type: `String`
- Description: `The prefix for the location in the S3 bucket. If you don't specify a prefix, the access logs are stored in the root of the bucket.`

#### UnHealthyThreshold
- Default: `3`
- Type: `String`
- Description: `Consecutive failed checks before marking instance unhealthy.`

#### HealthyThreshold
- Default: `3`
- Type: `String`
- Description: `Consecutive successful checks before marking instance healthy.`

#### ASGTargets
- Default: `true`
- Type: `String`
- Description: `Are the targets part of an auto scaling group.`
- AllowedValues: `['true', 'false']`

#### SSLIdCert
- Default: ``
- ConstraintDescription: `Must be an existing SSL Name.`
- Type: `String`
- Description: `SSL Certificate Name. Full ARN required.`

#### CrossZone
- Default: `true`
- Type: `String`
- Description: `Whether cross-zone load balancing is enabled for the load balancer.`
- AllowedValues: `['true', 'false']`

#### CookieExpirationPeriod
- Default: ``
- Type: `String`
- Description: `Generates a stickiness policy with sticky session lifetimes controlled by a specified expiration period. Leave blank not to use.`

#### LogRetention
- Default: `14`
- MinValue: `1`
- Type: `Number`
- Description: `The number of days to retain load balancer logs.  Parameter is ignored if not creating a new S3 bucket.`
- MaxValue: `999`

#### InternalZoneId
- Default: ``
- Type: `String`
- Description: `The Route53 Internal Hosted Zone ID`

#### LoadBalancerPort2
- Default: `443`
- Type: `String`
- Description: `Specifies the external load balancer port number.`

#### Instances
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A list of EC2 instance IDs for the load balancer. Use when not assigned to auto scale group.`

#### EnableListener2
- Default: `False`
- Type: `String`
- Description: `Enable Primary Listener on the Load Balancer`
- AllowedValues: `['True', 'False']`

#### LogAccessControl
- Default: `BucketOwnerFullControl`
- ConstraintDescription: `Must be either AuthenticatedRead, AwsExecRead, BucketOwnerRead, BucketOwnerFullControl, LogDeliveryWrite, Private, PublicRead or PublicReadWrite.`
- Type: `String`
- Description: `Define ACL for Bucket`
- AllowedValues: `['AuthenticatedRead', 'AwsExecRead', 'BucketOwnerRead', 'BucketOwnerFullControl', 'LogDeliveryWrite', 'Private', 'PublicRead', 'PublicReadWrite']`

#### S3BucketName
- Default: ``
- ConstraintDescription: `The bucket name must contain only lowercase letters, numbers, periods (.), and dashes (-).`
- Type: `String`
- Description: `The name of the bucket to use for CLB logs. Must be unique.`

#### TimeOut
- Default: `0`
- MinValue: `0`
- Type: `Number`
- Description: `The time (in seconds) that a connection to the load balancer can remain idle, which means no data is sent over the connection. After the specified time, the load balancer closes the connection.`
- MaxValue: `3600`

#### LoadBalancerName
- Default: `NewCLB`
- AllowedPattern: `^[^-][\w-]+`
- Type: `String`
- Description: `This name must be unique within your set of load balancers for the region.`
- MaxLength: `32`

#### InstanceProtocol2
- Default: `HTTP`
- Type: `String`
- Description: `Specifies the protocol to use for routing traffic to back-end instances HTTP / HTTPS / TCP / SSL.`
- AllowedValues: `['HTTP', 'HTTPS', 'TCP', 'SSL']`

#### InstanceProtocol1
- Default: `HTTP`
- Type: `String`
- Description: `Specifies the protocol to use for routing traffic to back-end instances HTTP / HTTPS / TCP / SSL.`
- AllowedValues: `['HTTP', 'HTTPS', 'TCP', 'SSL']`

### Outputs
- `UnHealthyHostCountAlarm`
- `S3BucketName`
- `CLB`

### Alarms
#### UnHealthyHostCountAlarm
- Description: Unhealthy Host count is above threshold, creating ticket.
- Metric: UnHealthyHostCount
- Threshold: 1
- Actions: `{'Fn::If': ['RackspaceAlarmsEnabled', {'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-emergency'}, {'Ref': 'AWS::NoValue'}]}`
