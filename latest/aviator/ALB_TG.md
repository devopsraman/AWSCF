AlbTg FAWS Template
===================
ALB_TG.template - Elastic Load Balancer v2 (Target Group) template.
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

#### HealthyThresholdCount
- Default: `5`
- MinValue: `2`
- Type: `Number`
- Description: `The number of consecutive successful health checks that are required before an unhealthy target is considered healthy.`
- MaxValue: `10`

#### ListenerRule1Path
- Default: ``
- Type: `String`
- Description: `A host header or a single URI path, as defined by ListenerRule1Condition.`

#### ListenerRule2Priority
- Default: `20`
- Type: `String`
- Description: `The priority to use for this rule.`

#### EnableRackspaceTicket
- Default: `False`
- Type: `String`
- Description: `Specifies whether alarms will generate Rackspace tickets`
- AllowedValues: `['False', 'True']`

#### CookieDuration
- Default: `86400`
- MinValue: `1`
- Type: `Number`
- Description: `The time period, in seconds, during which requests from a client should be routed to the same target.`
- MaxValue: `604800`

#### ListenerRule3Path
- Default: ``
- Type: `String`
- Description: `A host header or a single URI path, as defined by ListenerRule3Condition.`

#### HealthCheckPort
- Default: `traffic-port`
- Type: `String`
- Description: ``

#### TargetGroupType
- Default: `ASG`
- Type: `String`
- Description: `The type of target. (ASG\ECS or Instance)`
- AllowedValues: `['ASG', 'Instance']`

#### ListenerRule1Condition
- Default: `path-pattern`
- Type: `String`
- Description: `Should this rule use host headers, or a URI path.`
- AllowedValues: `['path-pattern', 'host-header']`

#### ListenerRule4Path
- Default: ``
- Type: `String`
- Description: `A host header or a single URI path, as defined by ListenerRule4Condition.`

#### TargetGroupProtocol
- Default: `HTTP`
- Type: `String`
- Description: `The protocol to use for routing traffic to the targets.`
- AllowedValues: `['HTTP', 'HTTPS']`

#### HealthCheckPath
- Default: `/`
- Type: `String`
- Description: `The ping path destination where Elastic Load Balancing sends health check requests.`
- MaxLength: `1024`

#### ListenerRule2Path
- Default: ``
- Type: `String`
- Description: `A host header or a single URI path, as defined by ListenerRule2Condition.`

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

#### ListenerRule3Condition
- Default: `path-pattern`
- Type: `String`
- Description: `Should this rule use host headers, or a URI path.`
- AllowedValues: `['path-pattern', 'host-header']`

#### ListenerRule2Condition
- Default: `path-pattern`
- Type: `String`
- Description: `Should this rule use host headers, or a URI path.`
- AllowedValues: `['path-pattern', 'host-header']`

#### HealthCheckIntervalSeconds
- Default: `30`
- MinValue: `5`
- Type: `Number`
- Description: `The approximate number of seconds between health checks for an individual target.`
- MaxValue: `300`

#### AttributeDelayTimeout
- Default: `30`
- MinValue: `0`
- Type: `Number`
- Description: `The amount time for Elastic Load Balancing to wait before changing the state of a deregistering target from draining to unused.`
- MaxValue: `3600`

#### MatcherCode
- Default: `200-299`
- Type: `String`
- Description: `The HTTP codes. The default value is 200.`

#### HealthCheckProtocol
- Default: `HTTP`
- Type: `String`
- Description: `The protocol that the load balancer uses when performing health checks on the targets, such as HTTP or HTTPS.`
- AllowedValues: `['HTTP', 'HTTPS']`

#### ListenerRule4Priority
- Default: `40`
- Type: `String`
- Description: `The priority to use for this rule.`

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

#### ListenerRule1Priority
- Default: `10`
- Type: `String`
- Description: `The priority to use for this rule.`

#### TargetGroupNameVersion
- Default: `v00`
- Type: `String`
- Description: `NOTE: This needs to increment on update with new Target Group.`

#### ListenerRule3Priority
- Default: `30`
- Type: `String`
- Description: `The priority to use for this rule.`

#### UnhealthyThresholdCount
- Default: `2`
- MinValue: `2`
- Type: `Number`
- Description: `The number of consecutive failed health checks that are required before a target is considered unhealthy.`
- MaxValue: `10`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### Listener1Arn
- Default: ``
- Type: `String`
- Description: `ARN of the first ALB listener. (OPTIONAL)`

#### ListenerRule4Condition
- Default: `path-pattern`
- Type: `String`
- Description: `Should this rule use host headers, or a URI path.`
- AllowedValues: `['path-pattern', 'host-header']`

#### TargetGroupTargetPort2
- Default: `80`
- MinValue: `1`
- Type: `Number`
- Description: `The port number on which the target is listening for traffic.`
- MaxValue: `65535`

#### LoadBalancerName
- Type: `String`
- Description: `The full name for the load balancer.`

#### TargetGroupTargetPort3
- Default: `80`
- MinValue: `1`
- Type: `Number`
- Description: `The port number on which the target is listening for traffic.`
- MaxValue: `65535`

#### TargetGroupTargetPort1
- Default: `80`
- MinValue: `1`
- Type: `Number`
- Description: `The port number on which the target is listening for traffic.`
- MaxValue: `65535`

#### TargetGroupName
- Default: `ALB-TargetGroup`
- Type: `String`
- Description: `A name for the Target Group.`

#### Listener2Arn
- Default: ``
- Type: `String`
- Description: `ARN of the second ALB listener. (OPTIONAL)`

### Outputs
- `ELBv2TargetGroupInstance`
- `UnHealthyHostCountAlarm`
- `ELBv2TargetGroupASG`

### Alarms
#### UnHealthyHostCountAlarm
- Description: Unhealthy Host count is above threshold, creating ticket.
- Metric: UnHealthyHostCount
- Threshold: 1
- Actions: `{'Fn::If': ['RackspaceAlarmsEnabled', {'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-emergency'}, {'Ref': 'AWS::NoValue'}]}`
