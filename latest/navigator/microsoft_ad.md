MicrosoftAd FAWS Template
=========================
microsoft_ad.template - Template for AWS Microsoft AD resource.
### Parameters

#### Password
- Type: `String`
- NoEcho: `True`
- Description: `The password for the default administrative user, Admin.`

#### Name
- Type: `String`
- Description: `The fully qualified name for the Microsoft Active Directory in AWS, such as corp.example.com. The name doesn't need to be publicly resolvable; it will resolve inside your VPC only.`

#### SubnetIds
- Type: `List<AWS::EC2::Subnet::Id>`
- Description: `A list of at least two subnet IDs for the directory servers. Each subnet must be in different Availability Zones (AZs). AWS Directory Service creates a directory server and a DNS server in each subnet.`

#### VPCID
- Type: `AWS::EC2::VPC::Id`
- Description: `The VPC ID in which to create the Microsoft Active Directory server.`

#### EnableSso
- Default: `False`
- Type: `String`
- Description: `Whether to enable single sign-on for a Microsoft Active Directory in AWS. Single sign-on allows users in your directory to access certain AWS services from a computer joined to the directory without having to enter their credentials separately. If you don't specify a value, AWS CloudFormation disables single sign-on by default.`
- AllowedValues: `['True', 'False']`

#### ShortName
- Default: ``
- Type: `String`
- Description: `The NetBIOS name for your domain, such as CORP. If you don't specify a value, AWS Directory Service uses the first part of your directory DNS server name. For example, if your directory DNS server name is corp.example.com, AWS Directory Service specifies CORP for the NetBIOS name.`

#### CreateAlias
- Default: `False`
- Type: `String`
- Description: `A unique alias to assign to the Microsoft Active Directory in AWS. AWS Directory Service uses the alias to construct the access URL for the directory, such as http://alias.awsapps.com. By default, AWS CloudFormation does not create an alias.`
- AllowedValues: `['True', 'False']`

### Outputs
- `directoryId`
- `dnsIpAddresses`
- `directoryName`

### Alarms