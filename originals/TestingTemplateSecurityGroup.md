
## Description

Security Group template for the testing template.

#### Metadata


## Parameters

 * **Environment** - Application environment for which this network is being created. e.g. Development/Production.
  * Default: `Development`
 * **VPCID** - Select Virtual Private Cloud ID.

## Conditions


## Mappings


## Resources

 * **EFSSecurityGroup** - `AWS::EC2::SecurityGroup`
 * **ElasticCacheMemcacheSecurityGroup** - `AWS::EC2::SecurityGroup`
 * **ElasticCacheRedisSecurityGroup** - `AWS::EC2::SecurityGroup`
 * **MSSQLSecurityGroup** - `AWS::EC2::SecurityGroup`
 * **MySQLSecurityGroup** - `AWS::EC2::SecurityGroup`
 * **NFSSecurityGroup** - `AWS::EC2::SecurityGroup`
 * **PrivateRDPSecurityGroup** - `AWS::EC2::SecurityGroup`
 * **PrivateSSHSecurityGroup** - `AWS::EC2::SecurityGroup`
 * **PrivateWebSecurityGroup** - `AWS::EC2::SecurityGroup`
 * **PublicRDPSecurityGroup** - `AWS::EC2::SecurityGroup`
 * **PublicSSHSecurityGroup** - `AWS::EC2::SecurityGroup`
 * **PublicWebSecurityGroup** - `AWS::EC2::SecurityGroup`

## Outputs

 * **outputEFSSecurityGroup** - `{u'Fn::GetAtt': [u'EFSSecurityGroup', u'GroupId']}`
 * **outputElasticCacheMemcacheSecurityGroup** - `{u'Fn::GetAtt': [u'ElasticCacheMemcacheSecurityGroup', u'GroupId']}`
 * **outputElasticCacheRedisSecurityGroup** - `{u'Fn::GetAtt': [u'ElasticCacheRedisSecurityGroup', u'GroupId']}`
 * **outputMSSQLSecurityGroup** - `{u'Fn::GetAtt': [u'MSSQLSecurityGroup', u'GroupId']}`
 * **outputMySQLSecurityGroup** - `{u'Fn::GetAtt': [u'MySQLSecurityGroup', u'GroupId']}`
 * **outputNFSSecurityGroup** - `{u'Fn::GetAtt': [u'NFSSecurityGroup', u'GroupId']}`
 * **outputPrivateRDPSecurityGroup** - `{u'Fn::GetAtt': [u'PrivateRDPSecurityGroup', u'GroupId']}`
 * **outputPrivateSSHSecurityGroup** - `{u'Fn::GetAtt': [u'PrivateSSHSecurityGroup', u'GroupId']}`
 * **outputPrivateWebSecurityGroup** - `{u'Fn::GetAtt': [u'PrivateWebSecurityGroup', u'GroupId']}`
 * **outputPublicRDPSecurityGroup** - `{u'Fn::GetAtt': [u'PublicRDPSecurityGroup', u'GroupId']}`
 * **outputPublicSSHSecurityGroup** - `{u'Fn::GetAtt': [u'PublicSSHSecurityGroup', u'GroupId']}`
 * **outputPublicWebSecurityGroup** - `{u'Fn::GetAtt': [u'PublicWebSecurityGroup', u'GroupId']}`