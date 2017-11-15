AlbWafAttachment FAWS Template
==============================
ALB_waf_attachment.template - Elastic Load Balancer v2 (Application Load Balancer) template.
### Parameters

#### VPCID
- Type: `AWS::EC2::VPC::Id`
- Description: `The VPC in which your targets are located.`

#### TargetGroupPort
- Default: `80`
- MinValue: `1`
- Type: `Number`
- Description: `The port on which the targets receive traffic.`
- MaxValue: `65535`

#### AttributeDelayTimeout
- Default: `30`
- MinValue: `0`
- Type: `Number`
- Description: `The amount time for Elastic Load Balancing to wait before changing the state of a deregistering target from draining to unused.`
- MaxValue: `3600`

#### Listener2SSL
- Default: ``
- Type: `String`
- Description: `The Amazon Resource Name (ARN) of the default certificate(s) to associate with listener 2. (OPTIONAL)`

#### HealthCheckIntervalSeconds
- Default: `30`
- MinValue: `5`
- Type: `Number`
- Description: `The approximate number of seconds between health checks for an individual target.`
- MaxValue: `300`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### Listener1SSL
- Default: ``
- Type: `String`
- Description: `The Amazon Resource Name (ARN) of the default certificate(s) to associate with listener 1. (OPTIONAL)`

#### InternalRecordName
- Default: ``
- Type: `String`
- Description: `Record Name for the new Resource Record in the Internal Hosted Zone`

#### Scheme
- Default: `internet-facing`
- Type: `String`
- Description: `Indicates whether the load balancer is Internet-facing or internal.`
- AllowedValues: `['internet-facing', 'internal']`

#### CookieDuration
- Default: `86400`
- MinValue: `1`
- Type: `Number`
- Description: `The time period, in seconds, during which requests from a client should be routed to the same target.`
- MaxValue: `604800`

#### Subnets
- Type: `List<AWS::EC2::Subnet::Id>`
- Description: `A list of at least two IDs of the subnets to associate with the load balancer.`

#### EnableRackspaceTicket
- Default: `False`
- Type: `String`
- Description: `Specifies whether alarms will generate Rackspace tickets`
- AllowedValues: `['False', 'True']`

#### Listener1Protocol
- Default: `HTTP`
- Type: `String`
- Description: `The protocol that clients must use to send requests to the listener.`
- AllowedValues: `['HTTP', 'HTTPS']`

#### TargetGroupTargetPort2
- Default: `80`
- MinValue: `1`
- Type: `Number`
- Description: `The port number on which the target is listening for traffic.`
- MaxValue: `65535`

#### TargetGroupType
- Default: `ASG`
- Type: `String`
- Description: `The type of target. (ASG\ECS or Instance)`
- AllowedValues: `['ASG', 'Instance']`

#### CreateLoggingBucket
- Default: `true`
- Type: `String`
- Description: `Create a new S3 logging bucket.`
- AllowedValues: `['true', 'false']`

#### TargetGroupProtocol
- Default: `HTTP`
- Type: `String`
- Description: `The protocol to use for routing traffic to the targets.`
- AllowedValues: `['HTTP', 'HTTPS']`

#### InternalZoneName
- Default: ``
- Type: `String`
- Description: `TLD for Internal Hosted Zone`

#### SecurityGroups
- Type: `List<AWS::EC2::SecurityGroup::Id>`
- Description: `A list of the IDs of the security groups to assign to the load balancer.`

#### HealthCheckProtocol
- Default: `HTTP`
- Type: `String`
- Description: `The protocol that the load balancer uses when performing health checks on the targets, such as HTTP or HTTPS.`
- AllowedValues: `['HTTP', 'HTTPS']`

#### TargetGroupTargetId1
- Default: ``
- Type: `String`
- Description: `The ID of the target, such as an EC2 instance ID.`

#### TargetGroupTargetId2
- Default: ``
- Type: `String`
- Description: `The ID of the target, such as an EC2 instance ID.`

#### TargetGroupTargetId3
- Default: ``
- Type: `String`
- Description: `The ID of the target, such as an EC2 instance ID.`

#### Listener2Port
- Default: `443`
- Type: `Number`
- Description: `The port on which the listener listens for requests.`

#### S3BucketPrefix
- Default: ``
- Type: `String`
- Description: `The prefix for the location in the S3 bucket. If you don't specify a prefix, the access logs are stored in the root of the bucket.`

#### Listener2Protocol
- Default: `HTTPS`
- Type: `String`
- Description: `The protocol that clients must use to send requests to the listener.`
- AllowedValues: `['HTTP', 'HTTPS']`

#### WebACLId
- Default: ``
- Type: `String`
- Description: `The unique identifier (ID) for the Web Application Firewall ACL. (OPTIONAL)`

#### MatcherCode
- Default: `200-299`
- Type: `String`
- Description: `The HTTP codes. The default value is 200.`

#### Listener1Port
- Default: `80`
- Type: `Number`
- Description: `The port on which the listener listens for requests.`

#### Listener2SSLPolicy
- Default: ``
- Type: `String`
- Description: `The security policy that defines which ciphers and protocols are supported. The default is the current predefined security policy. More information: http://docs.aws.amazon.com/elasticloadbalancing/latest/application/create-https-listener.html#describe-ssl-policies.`

#### LoadBalancerName
- Default: `ALB-LoadBalancer-Name`
- Type: `String`
- Description: `A name for the load balancer, which must be unique within your AWS account.`

#### HealthCheckPath
- Default: `/`
- Type: `String`
- Description: `The ping path destination where Elastic Load Balancing sends health check requests.`
- MaxLength: `1024`

#### HealthCheckTimeoutSeconds
- Default: `5`
- MinValue: `2`
- Type: `Number`
- Description: `The number of seconds to wait for a response before considering that a health check has failed.`
- MaxValue: `60`

#### AttributeStickinessEnabled
- Default: `true`
- Type: `String`
- ConstraintDescription: `Value must be either lowercase true or false.`
- Description: `Indicates whether sticky sessions are enabled.`
- AllowedValues: `['true', 'false']`

#### HealthCheckPort
- Default: `traffic-port`
- Type: `String`
- Description: ``

#### UnhealthyThresholdCount
- Default: `2`
- MinValue: `2`
- Type: `Number`
- Description: `The number of consecutive failed health checks that are required before a target is considered unhealthy.`
- MaxValue: `10`

#### S3LogDeletionProtection
- Default: `false`
- Type: `String`
- ConstraintDescription: `Value must be either lowercase true or false.`
- Description: `Indicates whether deletion protection is enabled.`
- AllowedValues: `['true', 'false']`

#### HealthyThresholdCount
- Default: `5`
- MinValue: `2`
- Type: `Number`
- Description: `The number of consecutive successful health checks that are required before an unhealthy target is considered healthy.`
- MaxValue: `10`

#### LogRetention
- Default: `14`
- MinValue: `1`
- Type: `Number`
- Description: `The number of days to retain load balancer logs.  Parameter is ignored if not creating a new S3 bucket.`
- MaxValue: `999`

#### Listener1SSLPolicy
- Default: ``
- Type: `String`
- Description: `The security policy that defines which ciphers and protocols are supported. The default is the current predefined security policy. More information: http://docs.aws.amazon.com/elasticloadbalancing/latest/application/create-https-listener.html#describe-ssl-policies.`

#### EnableListener1
- Default: `True`
- Type: `String`
- Description: `Enable Primary Listener on the Load Balancer`
- AllowedValues: `['True', 'False']`

#### EnableListener2
- Default: `False`
- Type: `String`
- Description: `Enable Primary Listener on the Load Balancer`
- AllowedValues: `['True', 'False']`

#### LogAccessControl
- Default: `BucketOwnerFullControl`
- Type: `String`
- ConstraintDescription: `Must be either AuthenticatedRead, AwsExecRead, BucketOwnerRead, BucketOwnerFullControl, LogDeliveryWrite, Private, PublicRead or PublicReadWrite.`
- Description: `Define ACL for Bucket.`
- AllowedValues: `['AuthenticatedRead', 'AwsExecRead', 'BucketOwnerRead', 'BucketOwnerFullControl', 'LogDeliveryWrite', 'Private', 'PublicRead', 'PublicReadWrite']`

#### S3BucketName
- Default: ``
- Type: `String`
- Description: `The name of the S3 bucket for the access logs.`

#### TimeOut
- Default: `60`
- MinValue: `1`
- Type: `Number`
- Description: `The idle timeout value, in seconds. The valid range is 1-3600. The default is 60 seconds.`
- MaxValue: `3600`

#### ListenerSNICertificates
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A comma delimited list of Amazon Resource Names (ARNs).  Each ARN should point to an SSL certificate(s) to associate with any listener assigned a default certificate.`

#### ListenerSNICertificatesCount
- Default: `0`
- Type: `String`
- Description: `The number of additional SNI certificate ARNs provided.  If more than 5 are required, please use ALB_ListenerCertificate.template`
- AllowedValues: `[0, 1, 2, 3, 4, 5]`

#### LoadBalancerNameVersion
- Default: `v00`
- Type: `String`
- Description: `NOTE: This needs to increment on update with new ALB.`

#### InternalZoneId
- Default: ``
- Type: `String`
- Description: `The Route53 Internal Hosted Zone ID`

#### TargetGroupTargetPort1
- Default: `80`
- MinValue: `1`
- Type: `Number`
- Description: `The port number on which the target is listening for traffic.`
- MaxValue: `65535`

#### TargetGroupName
- Default: `ALB-TargetGroup`
- Type: `String`
- Description: `A name for the Default Target Group.`

#### TargetGroupTargetPort3
- Default: `80`
- MinValue: `1`
- Type: `Number`
- Description: `The port number on which the target is listening for traffic.`
- MaxValue: `65535`

### Outputs
- `ELBv2TargetGroupInstance`
- `ELBv2LoadBalancerFullName`
- `ELBv2`
- `ELBv2TargetGroupASG`
- `S3BucketName`
- `UnHealthyHostCountAlarm`
- `ELBv2Listener2`
- `ELBv2Listener1`

### Alarms
#### UnHealthyHostCountAlarm
- Description: Unhealthy Host count is above threshold, creating ticket.
- Metric: UnHealthyHostCount
- Threshold: 1
- Actions: `{'Fn::If': ['RackspaceAlarmsEnabled', {'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-emergency'}, {'Ref': 'AWS::NoValue'}]}`
