VpcPeer FAWS Template
=====================
Rackspace Hosting - Create a VPC Peering Template
### Parameters

#### VPCID
- Type: `AWS::EC2::VPC::Id`
- Description: `Select Virtual Private Cloud ID`

#### VpcRoutingTables
- Type: `CommaDelimitedList`
- Description: `Comma delimited list of VPC routing tables`

#### PeerRoutingTablesCount
- Default: `3`
- Type: `String`
- Description: `The number of peer routing tables to update.`
- AllowedValues: `[1, 2, 3, 4, 5]`

#### PeerVPCCIDRRange
- Default: `172.19.0.0/16`
- Type: `String`
- Description: `Peer VPC CIDR Range e.g. 172.19.0.0/16`

#### PeerOwnerId
- AllowedPattern: `^[0-9]*$`
- Default: ``
- Type: `String`
- Description: `The AWS account ID of the owner of the VPC that you want to peer with`
- ConstraintDescription: `Must be a numeric account ID.`

#### PeerVPCID
- Type: `String`
- Description: `Existing VPC Id to peer to`

#### VPCCIDRRange
- Default: `172.18.0.0/16`
- Type: `String`
- Description: `VPC CIDR Range e.g. 172.18.0.0/16`

#### VpcRoutingTablesCount
- Default: `3`
- Type: `String`
- Description: `The number of vpc routing tables to update.`
- AllowedValues: `[1, 2, 3, 4, 5]`

#### PeerRoutingTables
- Type: `CommaDelimitedList`
- Description: `Comma delimited list of Peer routing tables`

#### PeerRoleArn
- AllowedPattern: `^(arn:aws:iam::[0-9]+:role/.+)?$`
- Default: ``
- Type: `String`
- Description: `The Amazon Resource Name (ARN) of the VPC peer role for the peering connection in another AWS account.`
- ConstraintDescription: `Must match the pattern arn:aws:iam::[0-9]+:role/.+`

### Outputs

### Alarms