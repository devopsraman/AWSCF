
## Description

Testing template for AWS Microsoft AD resource.

#### Metadata

 * **AWS::CloudFormation::Interface**: {u'ParameterGroups': [{u'Parameters': [u'Name', u'Password', u'VpcId', u'SubnetIds'], u'Label': {u'default': u'Required Configuration'}}, {u'Parameters': [u'ShortName', u'CreateAlias', u'EnableSso'], u'Label': {u'default': u'Optional Configuration'}}]}

## Parameters

 * **CreateAlias** - A unique alias to assign to the Microsoft Active Directory in AWS. AWS Directory Service uses the alias to construct the access URL for the directory, such as http://alias.awsapps.com. By default, AWS CloudFormation does not create an alias.
  * Default: `False`
 * **EnableSso** - Whether to enable single sign-on for a Microsoft Active Directory in AWS. Single sign-on allows users in your directory to access certain AWS services from a computer joined to the directory without having to enter their credentials separately. If you don't specify a value, AWS CloudFormation disables single sign-on by default.
  * Default: `False`
 * **Name** - The fully qualified name for the Microsoft Active Directory in AWS, such as corp.example.com. The name doesn't need to be publicly resolvable; it will resolve inside your VPC only.
 * **Password** - The password for the default administrative user, Admin.
 * **ShortName** - The NetBIOS name for your domain, such as CORP. If you don't specify a value, AWS Directory Service uses the first part of your directory DNS server name. For example, if your directory DNS server name is corp.example.com, AWS Directory Service specifies CORP for the NetBIOS name.
  * Default: ``
 * **SubnetIds** - A list of at least two subnet IDs for the directory servers. Each subnet must be in different Availability Zones (AZs). AWS Directory Service creates a directory server and a DNS server in each subnet.
 * **VpcId** - The VPC ID in which to create the Microsoft Active Directory server.

## Conditions

 * **doCreateAlias** - `{u'Fn::Equals': [{u'Ref': u'CreateAlias'}, u'True']}`
 * **doEnableSso** - `{u'Fn::Equals': [{u'Ref': u'EnableSso'}, u'True']}`
 * **useShortName** - `{u'Fn::Not': [{u'Fn::Equals': [{u'Ref': u'ShortName'}, u'']}]}`

## Resources

 * **MicrosoftAD** - `AWS::DirectoryService::MicrosoftAD`

## Outputs

 * **directoryId** - `{u'Ref': u'MicrosoftAD'}`
 * **directoryName** - `{u'Ref': u'Name'}`
 * **dnsIpAddresses** - `{u'Fn::Join': [u',', [{u'Fn::Select': [u'0', {u'Fn::GetAtt': [u'MicrosoftAD', u'DnsIpAddresses']}]}, {u'Fn::Select': [u'1', {u'Fn::GetAtt': [u'MicrosoftAD', u'DnsIpAddresses']}]}]]}`