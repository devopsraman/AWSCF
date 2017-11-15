BaseNetwork FAWS Template
=========================
base_network.template - Base VPC, Network, and NAT gateways. Please be aware that this template will create resources for which you will be charged.
### Parameters

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### InstanceTenancy
- Default: `default`
- Type: `String`
- ConstraintDescription: `Must be either 'default' for multi-tenant hypervisor or 'dedicated' for single tenant hypervisor.`
- Description: `VPC default for single tenant (dedicated) vs multi-tenant (default) hypervisor. Overrides instance level tenancy option.`
- AllowedValues: `['default', 'dedicated']`

#### AvailabilityZoneCount
- Default: `2 AZs :: 4 Subnets`
- ConstraintDescription: `Must be either 2 or 3.`
- Type: `String`
- Description: `Number of Availability Zones (3 AZs needs a use case)`
- AllowedValues: `['1 AZ :: 2 Subnets', '2 AZs :: 4 Subnets', '3 AZs :: 6 Subnets']`

#### PublicSubnetAZ1
- ConstraintDescription: `Must be a valid CIDR range of the form x.x.x.x/x`
- Description: `Public IP subnet used for AZ1.  Default "172.18.168.0/22"`
- Default: `172.18.168.0/22`
- MinLength: `9`
- AllowedPattern: `^([0-9]+\.){3}[0-9]+\/[0-9]+$`
- MaxLength: `18`
- Type: `String`

#### PrivateSubnetAZ1
- ConstraintDescription: `Must be a valid CIDR range of the form x.x.x.x/x`
- Description: `Private IP subnet used for AZ1.  Default "172.18.0.0/21"`
- Default: `172.18.0.0/21`
- MinLength: `9`
- AllowedPattern: `^([0-9]+\.){3}[0-9]+\/[0-9]+$`
- MaxLength: `18`
- Type: `String`

#### PrivateSubnetAZ3
- ConstraintDescription: `Must be a valid CIDR range of the form x.x.x.x/x`
- Description: `(Conditional) Private IP subnet used for AZ3.  Default "172.18.16.0/21"`
- Default: `172.18.16.0/21`
- MinLength: `9`
- AllowedPattern: `^([0-9]+\.){3}[0-9]+\/[0-9]+$`
- MaxLength: `18`
- Type: `String`

#### PrivateSubnetAZ2
- ConstraintDescription: `Must be a valid CIDR range of the form x.x.x.x/x`
- Description: `Private IP subnet used for AZ2.  Default "172.18.8.0/21"`
- Default: `172.18.8.0/21`
- MinLength: `9`
- AllowedPattern: `^([0-9]+\.){3}[0-9]+\/[0-9]+$`
- MaxLength: `18`
- Type: `String`

#### CustomAZList
- Default: ``
- Type: `CommaDelimitedList`
- Description: `Ordered list of Availability Zones to use for the VPC.  If not provided, the full AZ list for the region is used. (OPTIONAL)`

#### SecondaryCIDRRange
- Description: `The secondary IP address space to be used for this VPC, in CIDR notation.  (OPTIONAL)`
- Default: ``
- Type: `String`
- AllowedPattern: `^([0-9]+\.){3}[0-9]+\/(1[6-9]|2[0-8])$||^$`
- MaxLength: `18`
- ConstraintDescription: `Must be a valid CIDR range of the form x.x.x.x/x between /16 and /28`

#### PublicSubnetAZ2
- ConstraintDescription: `Must be a valid CIDR range of the form x.x.x.x/x`
- Description: `Public IP subnet used for AZ2.  Default "172.18.172.0/22"`
- Default: `172.18.172.0/22`
- MinLength: `9`
- AllowedPattern: `^([0-9]+\.){3}[0-9]+\/[0-9]+$`
- MaxLength: `18`
- Type: `String`

#### CustomDNSList
- Default: `AmazonProvidedDNS`
- Type: `CommaDelimitedList`
- Description: `List of DNS Servers to use for the VPC.  'AmazonProvidedDNS' can be used to reference the AWS provided DNS servers. (OPTIONAL)`

#### CIDRRange
- ConstraintDescription: `Must be a valid CIDR range of the form x.x.x.x/x`
- Description: `The IP address space to be used for this VPC, in CIDR notation`
- Default: `172.18.0.0/16`
- MinLength: `9`
- AllowedPattern: `^([0-9]+\.){3}[0-9]+\/[0-9]+$`
- MaxLength: `18`
- Type: `String`

#### PublicSubnetAZ3
- ConstraintDescription: `Must be a valid CIDR range of the form x.x.x.x/x`
- Description: `(Conditional) Public IP subnet used for AZ3.  Default "172.18.176.0/22"`
- Default: `172.18.176.0/22`
- MinLength: `9`
- AllowedPattern: `^([0-9]+\.){3}[0-9]+\/[0-9]+$`
- MaxLength: `18`
- Type: `String`

#### VPNGateway
- Default: `False`
- Type: `String`
- Description: `Creates a virtual private gateway. A virtual private gateway is the VPC-side endpoint for your VPN connection.`
- AllowedValues: `['True', 'False']`

#### CustomDomainName
- Default: ``
- Type: `String`
- Description: `The custom Domain name to use for the VPC.  Leave blank to use the default generated domain name.  (OPTIONAL)`

### Outputs
- `VPCID`
- `SubnetPrivateAZ3`
- `SubnetPrivateAZ2`
- `SubnetPrivateAZ1`
- `SubnetPublicAZ3`
- `PrivateSubnets`
- `Environment`
- `CIDRRange`
- `SubnetPublicAZ1`
- `SubnetPublicAZ2`
- `PublicSubnets`
- `DefaultSG`
- `VPNGateway`
- `RouteTablePrivateAZ1`
- `RouteTablePrivateAZ3`
- `RouteTablePrivateAZ2`
- `ElasticIP1`
- `ElasticIP2`
- `ElasticIP3`
- `RouteTablePublic`
- `CidrBlockAssociations`
- `RouteTables`

### Alarms