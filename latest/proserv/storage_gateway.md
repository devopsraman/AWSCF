StorageGateway FAWS Template
============================
storage_gateway.template - Deploys Storage Gateway w/ EIP and autorecovery into existing VPC
### Parameters

#### PubSubnet
- Type: `AWS::EC2::Subnet::Id`
- Description: `Public Subnet to allow for access to instance for activation.`

#### StorageGatewayType
- Default: `FileGateway`
- Type: `String`
- Description: `The type of storage gateway appliance to be built.`
- AllowedValues: `['FileGateway', 'VolumeGateway', 'TapeGateway']`

#### UploadBufferVolumeSize
- Default: `150`
- Type: `String`
- Description: `Select Storage Gateway Upload Buffer Storage Volume Size in GB.  (Unused with File Gateways)`

#### EBSOptimized
- Default: `True`
- Type: `String`
- Description: `Use EBS Optimized.`
- AllowedValues: `['False', 'True']`

#### InstanceRoleManagedPolicyArns
- Default: ``
- Type: `String`
- Description: `A comma delimited list of IAM policy ARNs for the InstanceRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### AdminCIDR
- Type: `String`
- Description: `The IP address space that will manage the Storage Gateway, in CIDR notation`
- MinLength: `9`
- AllowedPattern: `^([0-9]+\.){3}[0-9]+\/[0-9]+$`
- MaxLength: `18`
- ConstraintDescription: `Must be a valid CIDR range of the form x.x.x.x/x`

#### KeyName
- Type: `AWS::EC2::KeyPair::KeyName`
- Description: `Name of an existing EC2 KeyPair to enable SSH access to the instances.`

#### DetailedMonitoring
- Default: `True`
- Type: `String`
- Description: `Enable Detailed Monitoring.`
- AllowedValues: `['False', 'True']`

#### VPC
- Type: `AWS::EC2::VPC::Id`
- Description: `VPC to launch into.`

#### EbsVolumeType
- Default: `gp2`
- Type: `String`
- Description: `Select EBS Volume Type.`
- AllowedValues: `['io1', 'standard', 'gp2']`

#### CacheVolumeSize
- Default: `150`
- Type: `String`
- Description: `Select Storage Gateway Cache Storage Volume Size in GB.`

#### EIPAllocationId
- Default: ``
- Type: `String`
- Description: `The AllocationId of an existing EIP you want to associate with the instance (optional).`

#### TenType
- Default: `default`
- Type: `String`
- Description: `Preferred EC2 tenancy type (default, dedicated instance or full host).`
- AllowedValues: `['default', 'dedicated', 'host']`

#### Iops
- Default: `0`
- Type: `Number`
- Description: `Iops value required for use with io1 EBS volumes. This value should be 3 times the EBS volume size`

#### InstanceType
- Default: `m4.xlarge`
- ConstraintDescription: `Must be a valid EC2 instance type. Default is m4.xlarge`
- Type: `String`
- Description: `Select instance type`
- AllowedValues: `['m4.xlarge', 'm4.2xlarge', 'm4.4xlarge', 'm4.10xlarge', 'm4.16xlarge', 'm3.xlarge', 'm3.2xlarge', 'c4.xlarge', 'c4.2xlarge', 'c4.4xlarge', 'c4.8xlarge', 'c3.xlarge', 'c3.2xlarge', 'c3.4xlarge', 'c3.8xlarge', 'r3.xlarge', 'r3.2xlarge', 'r3.4xlarge', 'r3.8xlarge', 'd2.xlarge', 'd2.2xlarge', 'd2.4xlarge', 'd2.8xlarge', 'i2.xlarge', 'i2.2xlarge', 'i2.4xlarge', 'i2.8xlarge']`

### Outputs
- `URL`
- `PubIP`

### Alarms
#### StatusCheckRecoveryAlarm
- Description: Trigger a recovery when Storage Gateway instance status check fails for 2 consecutive minutes.
- Metric: StatusCheckFailed_System
- Threshold: 0
- Actions: `{'Fn::Join': ['', ['arn:aws:automate:', {'Ref': 'AWS::Region'}, ':ec2:recover']]}`
