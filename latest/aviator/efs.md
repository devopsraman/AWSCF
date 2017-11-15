Efs FAWS Template
=================
efs.template - Create an EFS Filesystem with up to 3 AZs and Mount Points
### Parameters

#### Subnets
- Type: `List<AWS::EC2::Subnet::Id>`
- Description: `Up to 3 Subnets for EFS Mount Points`

#### VolumeName
- Default: `myEFSvolume`
- MinLength: `1`
- Type: `String`
- Description: `The name to be used for the EFS volume`

#### EFSSecurityGroupList
- Type: `List<AWS::EC2::SecurityGroup::Id>`
- Description: `Security Group List assigned to the EFS FileSystem`

#### CWBurstCreditThreshold
- Default: `1000000000000`
- Type: `Number`
- Description: `The minimum EFS Burst Credit level before generating an alarm.`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### SubnetCount
- Default: `2`
- Type: `String`
- Description: `The number of private subnets selected.`
- AllowedValues: `[0, 1, 2, 3]`

#### EnableRackspaceTicket
- Default: `False`
- Type: `String`
- Description: `Specifies whether alarms will generate Rackspace tickets`
- AllowedValues: `['False', 'True']`

#### CWBurstCreditPeriod
- Default: `12`
- Type: `Number`
- Description: `The number of periods over which the EFS Burst Credit level is compared to the specified threshold.`

### Outputs
- `FileSystemID`
- `FileSystemDNS`

### Alarms
#### EFSBurstCredits
- Description: `{'Fn::Sub': 'EFS Burst Credits have dropped below ${CWBurstCreditThreshold} for ${CWBurstCreditPeriod} periods.'}`
- Metric: BurstCreditBalance
- Threshold: `{'Ref': 'CWBurstCreditThreshold'}`
- Actions: `{'Fn::If': ['RackspaceAlarmsEnabled', {'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-emergency'}, {'Ref': 'AWS::NoValue'}]}`
