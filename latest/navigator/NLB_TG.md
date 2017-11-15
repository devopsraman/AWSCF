NlbTg FAWS Template
===================
NLB_TG.template - Elastic Load Balancer v2 (Target Group) template.
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

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### EnableRackspaceTicket
- Default: `False`
- Type: `String`
- Description: `Specifies whether alarms will generate Rackspace tickets`
- AllowedValues: `['False', 'True']`

#### Listener1Port
- Default: `443`
- Type: `Number`
- Description: `The port on which the listener 1 listens for requests`

#### HealthCheckPort
- Default: `traffic-port`
- Type: `String`
- Description: ``

#### TargetGroupType
- Default: `ASG`
- Type: `String`
- Description: `The type of target. (ASG\ECS or Instance)`
- AllowedValues: `['ASG', 'Instance']`

#### HealthCheckPath
- Default: `/`
- Type: `String`
- Description: `The ping path destination where Elastic Load Balancing sends health check requests.`
- MaxLength: `1024`

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
- Default: `0`
- Type: `Number`
- Description: `The port on which the listener 2 listens for requests`

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

#### LoadBalancerArn
- Type: `String`
- Description: `The Amazon resource name (ARN) of the network load balancer.`

#### HealthCheckProtocol
- Default: `TCP`
- Type: `String`
- Description: `The protocol that the load balancer uses when performing health checks on the targets, such as HTTP or HTTPS.`
- AllowedValues: `['TCP', 'HTTP', 'HTTPS']`

#### TargetGroupNameVersion
- Default: `v00`
- Type: `String`
- Description: `NOTE: This needs to increment on update with new Target Group.`

#### HealthyThresholdCount
- Default: `5`
- MinValue: `2`
- Type: `Number`
- Description: `The number of consecutive successful health checks that are required before an unhealthy target is considered healthy.`
- MaxValue: `10`

#### TargetGroupName
- Default: `NLB-TargetGroup`
- Type: `String`
- Description: `A name for the Target Group.`

#### TargetGroupTargetPort1
- Default: `80`
- MinValue: `1`
- Type: `Number`
- Description: `The port number on which the target is listening for traffic.`
- MaxValue: `65535`

#### TargetGroupTargetPort2
- Default: `80`
- MinValue: `1`
- Type: `Number`
- Description: `The port number on which the target is listening for traffic.`
- MaxValue: `65535`

#### TargetGroupTargetPort3
- Default: `80`
- MinValue: `1`
- Type: `Number`
- Description: `The port number on which the target is listening for traffic.`
- MaxValue: `65535`

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
