Vpn FAWS Template
=================
vpn.template - VPN Setup Template. http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_VPN.html
### Parameters

#### StaticRoutes
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A comma separated list of internal subnets on the customer side. The subnets must be in valid CIDR notation(x.x.x.x/x). Ignored if Dynamic routing is used.`

#### VPCID
- Type: `AWS::EC2::VPC::Id`
- Description: `Select Virtual Private Cloud ID`

#### VPNRoutingType
- Default: `Static`
- Type: `String`
- Description: `Should Static or Dynamic routing be used for this VPN.`
- AllowedValues: `['Static', 'Dynamic']`

#### PropagateRoutesTo
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A comma separated list of route tables you would like to propagate the VPN Route to.`

#### StaticRoutesCount
- Default: `0`
- Type: `String`
- Description: `The number of CIDR ranges supplied in the StaticRoutes parameter.`
- AllowedValues: `[0, 1, 2, 3, 4, 5]`

#### CustomerIP
- ConstraintDescription: `Must be a valid CIDR range of the form x.x.x.x`
- Description: `The IP address of the Customer Endpoint`
- Default: `0.0.0.0`
- MinLength: `7`
- AllowedPattern: `^([0-9]+\.){3}[0-9]+`
- MaxLength: `18`
- Type: `String`

#### ExistingCGWId
- Default: ``
- Type: `String`
- Description: `Leave blank unless you already have an existing CGW attached in the VPC you're creating this VPN Connection in.`

#### NotificationTopic
- Default: ``
- Type: `String`
- Description: `SNS Topic ARN to notify if there are any alarms. OPTIONAL`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### ExistingVGWId
- Default: ``
- Type: `String`
- Description: `Leave blank unless you already have an existing VGW attached in the VPC you're creating this VPN Connection in.`

#### VpnEvaluations
- AllowedPattern: `([0-9]+)`
- Default: `10`
- Type: `String`
- Description: `The number of periods over which data is compared to the specified threshold.`
- ConstraintDescription: `Must be a valid integer.`

#### VpnPeriod
- AllowedPattern: `([0-9]+)`
- Default: `60`
- Type: `String`
- Description: `Time the specified statistic is applied. Must be in seconds that is also a multiple of 60.`
- ConstraintDescription: `Must be a valid integer.`

### Outputs
- `VirtualPrivateGatewayId`
- `CustomerGatewayId`

### Alarms
#### VPNStatus
- Description: `{'Fn::Sub': '${AWS::StackName} -VPN connection state.'}`
- Metric: TunnelState
- Threshold: 0
- Actions: `{'Fn::If': ['isNotification', {'Ref': 'NotificationTopic'}, {'Ref': 'AWS::NoValue'}]}`
