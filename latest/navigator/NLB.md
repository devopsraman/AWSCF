Nlb FAWS Template
=================
NLB.template - Elastic Load Balancer v2 (Network Load Balancer) template.
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

#### InternalRecordName
- Default: ``
- Type: `String`
- Description: `Record Name for the new Resource Record in the Internal Hosted Zone`

#### Scheme
- Default: `internet-facing`
- Type: `String`
- Description: `Indicates whether the load balancer is Internet-facing or internal.`
- AllowedValues: `['internet-facing', 'internal']`

#### Subnets
- Type: `List<AWS::EC2::Subnet::Id>`
- Description: `A list of at least two IDs of the subnets to associate with the load balancer.`

#### EnableRackspaceTicket
- Default: `False`
- Type: `String`
- Description: `Specifies whether alarms will generate Rackspace tickets`
- AllowedValues: `['False', 'True']`

#### HealthCheckPort
- Default: `traffic-port`
- Type: `String`
- Description: ``

#### TargetGroupType
- Default: `ASG`
- Type: `String`
- Description: `The type of target. (ASG\ECS or Instance)`
- AllowedValues: `['ASG', 'Instance']`

#### InternalZoneName
- Default: ``
- Type: `String`
- Description: `TLD for Internal Hosted Zone`

#### EIP1Allocation
- Default: `new`
- AllowedPattern: `^new$||^none$||^eipalloc-[a-z0-9]+$`
- Type: `String`
- Description: `An EIP Association to apply to the NLB in AZ 1.  Use the value 'new' to create a new EIP, and use the value of 'none' if the AZ is unused.`
- ConstraintDescription: `Must be none, new, or a valid EIP Allocation ID`

#### EIP3Allocation
- Default: `none`
- AllowedPattern: `^new$||^none$||^eipalloc-[a-z0-9]+$`
- Type: `String`
- Description: `An EIP Association to apply to the NLB in AZ 3.  Use the value 'new' to create a new EIP, and use the value of 'none' if the AZ is unused.`
- ConstraintDescription: `Must be none, new, or a valid EIP Allocation ID`

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

#### Listener1Port
- Default: `80`
- Type: `Number`
- Description: `The port on which the listener 1 listens for requests`

#### HealthCheckProtocol
- Default: `TCP`
- Type: `String`
- Description: `The protocol that the load balancer uses when performing health checks on the targets, such as HTTP or HTTPS.`
- AllowedValues: `['TCP', 'HTTP', 'HTTPS']`

#### LoadBalancerName
- Default: `NLB-LoadBalancer-Name`
- Type: `String`
- Description: `A name for the load balancer, which must be unique within your AWS account.`

#### DeletionProtection
- Default: `false`
- Type: `String`
- ConstraintDescription: `Value must be either lowercase true or false.`
- Description: `Indicates whether deletion protection is enabled.`
- AllowedValues: `['true', 'false']`

#### EIP2Allocation
- Default: `new`
- AllowedPattern: `^new$||^none$||^eipalloc-[a-z0-9]+$`
- Type: `String`
- Description: `An EIP Association to apply to the NLB in AZ 2.  Use the value 'new' to create a new EIP, and use the value of 'none' if the AZ is unused.`
- ConstraintDescription: `Must be none, new, or a valid EIP Allocation ID`

#### TargetGroupTargetPort2
- Default: `80`
- MinValue: `1`
- Type: `Number`
- Description: `The port number on which the target is listening for traffic.`
- MaxValue: `65535`

#### HealthyThresholdCount
- Default: `5`
- MinValue: `2`
- Type: `Number`
- Description: `The number of consecutive successful health checks that are required before an unhealthy target is considered healthy.`
- MaxValue: `10`

#### HealthCheckPath
- Default: `/`
- Type: `String`
- Description: `The ping path destination where Elastic Load Balancing sends health check requests.`
- MaxLength: `1024`

#### LoadBalancerNameVersion
- Default: `v00`
- Type: `String`
- Description: `NOTE: This needs to increment on update with new NLB.`

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
- Default: `NLB-TargetGroup`
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
- `NLBListener1`
- `NLBListener2`
- `NLBFullName`
- `ELBv2TargetGroupASG`
- `NLB`
- `UnHealthyHostCountAlarm`

### Alarms
#### UnHealthyHostCountAlarm
- Description: Unhealthy Host count is above threshold, creating ticket.
- Metric: UnHealthyHostCount
- Threshold: 1
- Actions: `{'Fn::If': ['RackspaceAlarmsEnabled', {'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-emergency'}, {'Ref': 'AWS::NoValue'}]}`
