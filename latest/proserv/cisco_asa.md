CiscoAsa FAWS Template
======================
cisco_asa.template - Deploys Cisco ASAv 9.6(2) w/ EIP and autorecovery into existing VPC
### Parameters

#### PubSubnet
- Type: `AWS::EC2::Subnet::Id`
- Description: `Public Subnet`

#### LicenseModel
- Default: `LicenseIncluded`
- Type: `String`
- Description: `Choose between BYOL (Bring Your Own License) and License Included license models. Remember to first subscribe the the appropriate Marketplace AMI!`
- AllowedValues: `['LicenseIncluded', 'BYOL']`

#### TerminationProtection
- Default: `Yes`
- Type: `String`
- Description: `Enable termination protection on the ASAv EC2 instances to avoid accidential ASAv termination?`
- AllowedValues: `['Yes', 'No']`

#### KeyName
- Type: `AWS::EC2::KeyPair::KeyName`
- Description: `Name of an existing EC2 KeyPair to enable SSH access to the instances.`

#### ASAvType
- Default: `ASAv10-1Gbps-c3.large`
- Type: `String`
- Description: `Performance required for ASAv instances.`
- AllowedValues: `['ASAv10-1Gbps-c3.large', 'ASAv10-1Gbps-c4.large', 'ASAv30-2Gbps-c3.xlarge', 'ASAv30-2Gbps-c4.xlarge']`

#### VPC
- Type: `AWS::EC2::VPC::Id`
- Description: `VPC to launch into.`

#### ASAvRoleManagedPolicyArns
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A comma delimited list of IAM policy ARNs for the ASAvRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### PriSubnet
- Type: `AWS::EC2::Subnet::Id`
- Description: `Private Subnet`

#### TenType
- Default: `default`
- Type: `String`
- Description: `Preferred EC2 tenancy type (default, dedicated instance or full host).`
- AllowedValues: `['default', 'dedicated', 'host']`

### Outputs
- `URL`
- `PubIP`

### Alarms
#### ASAvRecoveryAlarm
- Description: Trigger a recovery when ASAv instance status check fails for 15 consecutive minutes.
- Metric: StatusCheckFailed_System
- Threshold: 0
- Actions: `{'Fn::Join': ['', ['arn:aws:automate:', {'Ref': 'AWS::Region'}, ':ec2:recover']]}`
