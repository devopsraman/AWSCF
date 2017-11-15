Route53Internalzone FAWS Template
=================================
route53_internalzone.template - Route53 Internal Hosted Zone
### Parameters

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### InternalZoneName
- Default: ``
- Type: `String`
- Description: `TLD for Internal Hosted Zone`

#### VPCID
- Type: `AWS::EC2::VPC::Id`
- Description: `Select Virtual Private Cloud ID`

### Outputs
- `InternalHostedName`
- `InternalHostedZone`

### Alarms