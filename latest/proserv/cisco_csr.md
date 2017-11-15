CiscoCsr FAWS Template
======================
cisco_csr.template - Deploy a standalone Cisco CSR w/ EIP into existing VPC's public subnet. Creates automation account and saves keys to restricted bucket for separate Lambda functions.
### Parameters

#### SolutionHelperRoleManagedPolicyArns
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A comma delimited list of IAM policy ARNs for the SolutionHelperRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### PubSubnet
- Type: `AWS::EC2::Subnet::Id`
- Description: `Public Subnet`

#### LicenseModel
- Default: `LicenseIncluded`
- Type: `String`
- Description: `Choose between BYOL (Bring Your Own License) and License Included license models. Remember to first subscribe the the appropriate Marketplace AMI!`
- AllowedValues: `['LicenseIncluded', 'BYOL']`

#### S3Prefix
- Default: `csrconfig/`
- Type: `String`
- Description: `For config automation storage, the S3 prefix to append before S3 key names.`

#### CSRType
- Default: `500Mbps`
- Type: `String`
- Description: `Maximum network throughput required for CSR instances.`
- AllowedValues: `['250Mbps', '500Mbps', '1Gbps', '2Gbps', '4.5Gbps']`

#### TerminationProtection
- Default: `Yes`
- Type: `String`
- Description: `Enable termination protection on the CSR EC2 instances to avoid accidential CSR termination?`
- AllowedValues: `['Yes', 'No']`

#### KeyName
- Type: `AWS::EC2::KeyPair::KeyName`
- Description: `Name of an existing EC2 KeyPair to enable SSH access to the instances.`

#### VPC
- Type: `AWS::EC2::VPC::Id`
- Description: `VPC to launch into.`

#### CSRRoleManagedPolicyArns
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A comma delimited list of IAM policy ARNs for the CSRRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### TenType
- Default: `default`
- Type: `String`
- Description: `Preferred EC2 tenancy type (default, dedicated instance or full host).`
- AllowedValues: `['default', 'dedicated', 'host']`

### Outputs
- `URL`
- `PubIP`

### Alarms
#### CSRRecoveryAlarm
- Description: Trigger a recovery when CSR instance status check fails for 15 consecutive minutes.
- Metric: StatusCheckFailed_System
- Threshold: 0
- Actions: `{'Fn::Join': ['', ['arn:aws:automate:', {'Ref': 'AWS::Region'}, ':ec2:recover']]}`
