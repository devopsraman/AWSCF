VpcFlowLogs FAWS Template
=========================
vpc_flow_logs.template - VPC Flow Logs. http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-flowlog.html
### Parameters

#### ResourceType
- Default: `VPC`
- Type: `String`
- Description: `The type of resource that you specified in the ResourceId property. For example, if you specified a VPC ID for the ResourceId property, specify VPC for this property. For valid values, see the ResourceType parameter for the CreateFlowLogs action in the Amazon EC2 API Reference.`

#### ResourceId
- Type: `String`
- Description: `The ID of the subnet, network interface, or VPC for which you want to create a flow log.`

#### LogGroupName
- Default: `VPCFlowLogsGroup`
- Type: `String`
- Description: `The name of a new CloudWatch Logs log group where Amazon EC2 publishes your flow logs.`

#### InstanceRoleManagedPolicyArns
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A comma delimited list of IAM policy ARNs for the InstanceRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### TrafficType
- Default: `ALL`
- Type: `String`
- Description: `The type of traffic to log. You can log traffic that the resource accepts or rejects, or all traffic. For valid values, see the TrafficType parameter for the CreateFlowLogs action in the Amazon EC2 API Reference.`

#### RetentionInDays
- Default: `1`
- Type: `String`
- Description: `The number of days log events are kept in CloudWatch Logs. When a log event expires, CloudWatch Logs automatically deletes it.`

### Outputs
- `VPCFlowLogs`
- `LogGroup`

### Alarms