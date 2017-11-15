
## Description

Rackspace Hosting - Elastic Load Balancer v2 (Application Load Balancer) template.

#### Metadata

 * **AWS::CloudFormation::Interface**: {u'ParameterGroups': [{u'Parameters': [u'LoadBalancerName', u'Scheme', u'Environment', u'VpcId', u'Subnets', u'SecurityGroups', u'ELBTimeOut'], u'Label': {u'default': u'Application Load Balancer General Configuration.'}}, {u'Parameters': [u'TargetGroupType', u'TargetGroupName', u'TargetGroupMatcherCode'], u'Label': {u'default': u'Target Group Main Configuration.'}}, {u'Parameters': [u'TargetGroupPort', u'TargetGroupProtocol', u'TargetGroupCookieDuration', u'TargetGroupAttributeDelayTimeout', u'TargetGroupAttributeStickinessEnabled'], u'Label': {u'default': u'Target Group General Configuration.'}}, {u'Parameters': [u'TargetGroupUnhealthyThresholdCount', u'TargetGroupHealthyThresholdCount', u'TargetGroupHealthCheckTimeoutSeconds', u'TargetGroupHealthCheckProtocol', u'TargetGroupHealthCheckPort', u'TargetGroupHealthCheckPath', u'TargetGroupHealthCheckIntervalSeconds'], u'Label': {u'default': u'Target Group Health Monitoring Configuration.'}}, {u'Parameters': [u'TargetGroupTargetId1', u'TargetGroupTargetPort1', u'TargetGroupTargetId2', u'TargetGroupTargetPort2'], u'Label': {u'default': u'Target Group NON ASG Configuration (OPTIONAL)'}}, {u'Parameters': [u'ListenerCount'], u'Label': {u'default': u'Listener Configurations.'}}, {u'Parameters': [u'Listener1Port', u'Listener1SSL', u'Listener1Protocol', u'Listener1SSLPolicy'], u'Label': {u'default': u' Listener 1:'}}, {u'Parameters': [u'Listener2Port', u'Listener2SSL', u'Listener2Protocol', u'Listener2SSLPolicy'], u'Label': {u'default': u' Listener 2 (OPTIONAL):'}}, {u'Parameters': [u'Listener1RuleConditionValuesList', u'Listener1RulePriority'], u'Label': {u'default': u' Listener 1 Rule Configuration:'}}, {u'Parameters': [u'Listener2RuleConditionValuesList', u'Listener2RulePriority'], u'Label': {u'default': u' Listener 2 Rule Configuration (OPTIONAL):'}}, {u'Parameters': [u'CreateLoggingBucket', u'ELBS3BucketName', u'ELBS3BucketPrefix', u'ELBS3LogDeletionProtection', u'ELBLogAccessControl'], u'Label': {u'default': u'S3 Logging Configuration (OPTIONAL).'}}], u'ParameterLabels': {u'ListenerCount': {u'default': u'Number of listeners'}, u'ELBS3BucketName': {u'default': u'S3 bucket name'}, u'TargetGroupPort': {u'default': u'Target group port'}, u'ELBS3LogDeletionProtection': {u'default': u'S3 log protection'}, u'Listener2SSL': {u'default': u'Listener 2 SSL Certificate ARN'}, u'Listener1SSL': {u'default': u'Listener 1 SSL Certificate ARN'}, u'TargetGroupProtocol': {u'default': u'Target group protocol'}, u'TargetGroupHealthCheckPort': {u'default': u'Health check port'}, u'VpcId': {u'default': u'VPC id'}, u'Listener1Protocol': {u'default': u'Listener 1 protocol'}, u'TargetGroupTargetPort2': {u'default': u'Instance target 2 port'}, u'TargetGroupAttributeDelayTimeout': {u'default': u'Delay timeout'}, u'TargetGroupType': {u'default': u'Target group type'}, u'Listener2RuleConditionValuesList': {u'default': u'Listener 2 conditions'}, u'TargetGroupHealthCheckIntervalSeconds': {u'default': u'Health check interval'}, u'CreateLoggingBucket': {u'default': u'New S3 logging bucket'}, u'ELBLogAccessControl': {u'default': u'S3 log access control'}, u'SecurityGroups': {u'default': u'Security groups'}, u'TargetGroupHealthCheckPath': {u'default': u'Health check path'}, u'Listener1RulePriority': {u'default': u'Listener 1 priority'}, u'TargetGroupHealthCheckProtocol': {u'default': u'Health check protocol'}, u'TargetGroupTargetId2': {u'default': u'Instance target 2'}, u'Listener2Port': {u'default': u'Listener 2 port'}, u'Listener2Protocol': {u'default': u'Listener 2 protocol'}, u'Listener1Port': {u'default': u'Listener 1 port'}, u'Listener2SSLPolicy': {u'default': u'Listener 2 SSL policy'}, u'TargetGroupMatcherCode': {u'default': u'Target group match code'}, u'TargetGroupHealthyThresholdCount': {u'default': u'Healthy threshold count'}, u'TargetGroupTargetId1': {u'default': u'Instance target 1'}, u'ELBS3BucketPrefix': {u'default': u'S3 bucket prefix'}, u'TargetGroupCookieDuration': {u'default': u'Cookie duration'}, u'Listener1SSLPolicy': {u'default': u'Listener 1 SSL policy'}, u'EnableSSLonListener2': {u'default': u'Enable SSL on listener 2'}, u'ELBTimeOut': {u'default': u'Load balancer timeout'}, u'EnableSSLonListener1': {u'default': u'Enable SSL on listener 1'}, u'Listener1RuleConditionValuesList': {u'default': u'Listener 1 conditions'}, u'TargetGroupName': {u'default': u'Target group name'}, u'LoadBalancerName': {u'default': u'Load balancer name'}, u'TargetGroupUnhealthyThresholdCount': {u'default': u'Unhealthy threshold count'}, u'TargetGroupAttributeStickinessEnabled': {u'default': u'Stickiness enabled'}, u'TargetGroupTargetPort1': {u'default': u'Instance target 1 port'}, u'TargetGroupHealthCheckTimeoutSeconds': {u'default': u'Health check timeout'}, u'Listener2RulePriority': {u'default': u'Listener 2 priority'}}}
 * **Comments**: Generated by Ansible
 * **Version**: 1.0.0

## Parameters

 * **CreateLoggingBucket** - Create a new S3 logging bucket
  * Default: `false`
 * **ELBLogAccessControl** - Define ACL for Bucket
  * Default: `BucketOwnerFullControl`
  * Constraint: `Must be either AuthenticatedRead, AwsExecRead, BucketOwnerRead, BucketOwnerFullControl, LogDeliveryWrite, Private, PublicRead or PublicReadWrite.`
 * **ELBS3BucketName** - The name of the S3 bucket for the access logs.
  * Default: ``
 * **ELBS3BucketPrefix** - The prefix for the location in the S3 bucket. If you don't specify a prefix, the access logs are stored in the root of the bucket.
  * Default: ``
 * **ELBS3LogDeletionProtection** - Indicates whether deletion protection is enabled.
  * Default: `false`
  * Constraint: `Value must be either lowercase true or false.`
 * **ELBTimeOut** - The idle timeout value, in seconds. The valid range is 1-3600. The default is 60 seconds.
  * Default: `60`
 * **Environment** - Application environment for which this network is being created. e.g. Development/Production.
  * Default: `Development`
 * **Listener1Port** - The port on which the listener listens for requests.
  * Default: `80`
 * **Listener1Protocol** - The protocol that clients must use to send requests to the listener.
  * Default: `HTTP`
 * **Listener1RuleConditionValuesList** - The value for the field that you specified in the Field property.
  * Default: `*`
 * **Listener1RulePriority** - The priority for the rule. Elastic Load Balancing evaluates rules in priority order, from the lowest value to the highest value.
  * Default: `1`
 * **Listener1SSL** - The Amazon Resource Name (ARN) of the certificate(s) to associate with listener 1 (Optional).
  * Default: ``
 * **Listener1SSLPolicy** - The security policy that defines which ciphers and protocols are supported. The default is the current predefined security policy. More information: http://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-security-policy-options.html.
  * Default: ``
 * **Listener2Port** - The port on which the listener listens for requests.
  * Default: `0`
 * **Listener2Protocol** - The protocol that clients must use to send requests to the listener.
  * Default: `HTTP`
 * **Listener2RuleConditionValuesList** - The value for the field that you specified in the Field property.
  * Default: `*`
 * **Listener2RulePriority** - The priority for the rule. Elastic Load Balancing evaluates rules in priority order, from the lowest value to the highest value.
  * Default: `1`
 * **Listener2SSL** - The Amazon Resource Name (ARN) of the certificate(s) to associate with listener 3 (Optional).
  * Default: ``
 * **Listener2SSLPolicy** - The security policy that defines which ciphers and protocols are supported. The default is the current predefined security policy. More information: http://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-security-policy-options.html.
  * Default: ``
 * **ListenerCount** - The number of Listeners for this Load Balancer.
  * Default: `1`
 * **LoadBalancerName** - A name for the load balancer, which must be unique within your AWS account.
  * Default: `ALB-LoadBalancer-Name`
 * **Scheme** - Indicates whether the load balancer is Internet-facing or internal.
  * Default: `internet-facing`
 * **SecurityGroups** - A list of the IDs of the security groups to assign to the load balancer.
 * **Subnets** - A list of at least two IDs of the subnets to associate with the load balancer.
 * **TargetGroupAttributeDelayTimeout** - The amount time for Elastic Load Balancing to wait before changing the state of a deregistering target from draining to unused.
  * Default: `300`
 * **TargetGroupAttributeStickinessEnabled** - Indicates whether sticky sessions are enabled.
  * Default: `true`
  * Constraint: `Value must be either lowercase true or false.`
 * **TargetGroupCookieDuration** - The time period, in seconds, during which requests from a client should be routed to the same target.
  * Default: `86400`
 * **TargetGroupHealthCheckIntervalSeconds** - The approximate number of seconds between health checks for an individual target.
  * Default: `30`
 * **TargetGroupHealthCheckPath** - The ping path destination where Elastic Load Balancing sends health check requests.
  * Default: `/`
 * **TargetGroupHealthCheckPort** - 
  * Default: `traffic-port`
 * **TargetGroupHealthCheckProtocol** - The protocol that the load balancer uses when performing health checks on the targets, such as HTTP or HTTPS.
  * Default: `HTTP`
 * **TargetGroupHealthCheckTimeoutSeconds** - The number of seconds to wait for a response before considering that a health check has failed.
  * Default: `5`
 * **TargetGroupHealthyThresholdCount** - The number of consecutive successful health checks that are required before an unhealthy target is considered healthy.
  * Default: `5`
 * **TargetGroupMatcherCode** - The HTTP codes. The default value is 200.
  * Default: `200-299`
 * **TargetGroupName** - A name for the target group.
  * Default: `ALB-TargetGroup`
 * **TargetGroupPort** - The port on which the targets receive traffic.
  * Default: `80`
 * **TargetGroupProtocol** - The protocol to use for routing traffic to the targets.
  * Default: `HTTP`
 * **TargetGroupTargetId1** - The ID of the target, such as an EC2 instance ID.
  * Default: ``
 * **TargetGroupTargetId2** - The ID of the target, such as an EC2 instance ID.
  * Default: ``
 * **TargetGroupTargetPort1** - The port number on which the target is listening for traffic.
  * Default: `80`
 * **TargetGroupTargetPort2** - The port number on which the target is listening for traffic.
  * Default: `80`
 * **TargetGroupType** - The type of target (ASG or Instance).
  * Default: `ASG`
 * **TargetGroupUnhealthyThresholdCount** - The number of consecutive failed health checks that are required before a target is considered unhealthy.
  * Default: `2`
 * **VpcId** - The VPC in which your targets are located.

## Conditions

 * **Listener1Certs** - `{u'Fn::Not': [{u'Fn::Equals': [{u'Ref': u'Listener1SSL'}, u'']}]}`
 * **Listener2Certs** - `{u'Fn::Not': [{u'Fn::Equals': [{u'Ref': u'Listener1SSL'}, u'']}]}`
 * **NewS3Bucket** - `{u'Fn::Equals': [{u'Ref': u'CreateLoggingBucket'}, u'true']}`
 * **OneListener** - `{u'Fn::Equals': [{u'Ref': u'ListenerCount'}, u'1']}`
 * **S3LogsEnabled** - `{u'Fn::Not': [{u'Fn::Equals': [{u'Ref': u'ELBS3BucketName'}, u'']}]}`
 * **SSLPolicy1** - `{u'Fn::Not': [{u'Fn::Equals': [{u'Ref': u'Listener1SSLPolicy'}, u'']}]}`
 * **SSLPolicy2** - `{u'Fn::Not': [{u'Fn::Equals': [{u'Ref': u'Listener2SSLPolicy'}, u'']}]}`
 * **TargetTypeisASG** - `{u'Fn::Equals': [{u'Ref': u'TargetGroupType'}, u'ASG']}`
 * **TargetTypeisInstance** - `{u'Fn::Equals': [{u'Ref': u'TargetGroupType'}, u'Instance']}`
 * **TwoInstanceTargets** - `{u'Fn::Not': [{u'Fn::Equals': [{u'Ref': u'TargetGroupTargetId2'}, u'']}]}`
 * **TwoListener** - `{u'Fn::Equals': [{u'Ref': u'ListenerCount'}, u'2']}`

## Resources

 * **ELBS3LoggingBucketPolicy** - `AWS::S3::BucketPolicy`
 * **ELBv2** - `AWS::ElasticLoadBalancingV2::LoadBalancer`
 * **ELBv2Listener1** - `AWS::ElasticLoadBalancingV2::Listener`
 * **ELBv2Listener1Rule** - `AWS::ElasticLoadBalancingV2::ListenerRule`
 * **ELBv2Listener2** - `AWS::ElasticLoadBalancingV2::Listener`
 * **ELBv2Listener2Rule** - `AWS::ElasticLoadBalancingV2::ListenerRule`
 * **ELBv2TargetGroupASG** - `AWS::ElasticLoadBalancingV2::TargetGroup`
 * **ELBv2TargetGroupInstance** - `AWS::ElasticLoadBalancingV2::TargetGroup`
 * **S3BucketwithLogging** - `AWS::S3::Bucket`

## Outputs

 * **outputELBv2** - `{u'Ref': u'ELBv2'}`
 * **outputELBv2Listener1** - `{u'Ref': u'ELBv2Listener1'}`
 * **outputELBv2Listener1Rule** - `{u'Ref': u'ELBv2Listener1Rule'}`
 * **outputELBv2Listener2** - `{u'Ref': u'ELBv2Listener2'}`
 * **outputELBv2Listener2Rule** - `{u'Ref': u'ELBv2Listener2Rule'}`
 * **outputELBv2TargetGroupASG** - `{u'Ref': u'ELBv2TargetGroupASG'}`
 * **outputELBv2TargetGroupInstance** - `{u'Ref': u'ELBv2TargetGroupInstance'}`