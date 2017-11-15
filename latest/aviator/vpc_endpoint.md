VpcEndpoint FAWS Template
=========================
vpc_endpoint.template - Setup VPC endpoints for services that support them, as well as an all access IAM policy
### Parameters

#### RouteTableIdsList
- Type: `CommaDelimitedList`
- Description: `List of Route Table ID's for each AZ`

#### DynamoDBEndpointEnable
- Default: `True`
- Type: `String`
- Description: `Enable/Disable the DynamoDB VPC endpoint`
- AllowedValues: `['True', 'False']`

#### VPCID
- Type: `AWS::EC2::VPC::Id`
- Description: `Select Virtual Private Cloud ID`

#### S3EndpointEnable
- Default: `True`
- Type: `String`
- Description: `Enable/Disable the S3 VPC endpoint`
- AllowedValues: `['True', 'False']`

### Outputs
- `S3VPCEndpoint`
- `DynamoDBVPCEndpoint`

### Alarms