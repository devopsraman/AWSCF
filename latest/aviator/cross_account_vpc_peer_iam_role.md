CrossAccountVpcPeerIamRole FAWS Template
========================================
cross_account_vpc_peer_iam_role.template - Create a IAM role that will allow for cross account VPC peering
### Parameters

#### VpcRoutingTables
- Default: ``
- Type: `CommaDelimitedList`
- Description: `Comma delimited list of VPC routing tables.`

#### VPCCIDRRange
- Default: ``
- Type: `String`
- Description: `VPC CIDR Range e.g. 172.19.0.0/16`

#### VpcRoutingTablesCount
- Default: `3`
- Type: `String`
- Description: `The number of vpc routing tables to update.`
- AllowedValues: `[1, 2, 3, 4, 5]`

#### VpcPeeringConnectionId
- AllowedPattern: `^(pcx-.*)?`
- Default: ``
- Type: `String`
- Description: `The ID of the existing Peering Connection.`
- ConstraintDescription: `Must match the pattern pcx-XXXXXXXX`

#### AccountNumber
- AllowedPattern: `^[0-9]*$`
- ConstraintDescription: `Must be a numeric account ID.`
- Type: `String`
- Description: `Account ID for the VPC requester.`

### Outputs
- `CrossAccountRoleArn`

### Alarms