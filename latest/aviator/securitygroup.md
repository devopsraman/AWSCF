Securitygroup FAWS Template
===========================
securitygroup.template - Template for the security groups.
### Parameters

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### VPCID
- Type: `AWS::EC2::VPC::Id`
- Description: `Select Virtual Private Cloud ID.`

### Outputs
- `PublicRDPSecurityGroup`
- `ElasticCacheMemcacheSecurityGroup`
- `PublicSSHSecurityGroup`
- `PrivateWebSecurityGroup`
- `NFSSecurityGroup`
- `MySQLSecurityGroup`
- `MSSQLSecurityGroup`
- `PrivateSSHSecurityGroup`
- `PrivateECSSecurityGroup`
- `EFSSecurityGroup`
- `PublicWebSecurityGroup`
- `OracleSecurityGroup`
- `RedshiftSecurityGroup`
- `ElasticCacheRedisSecurityGroup`
- `PostgresSecurityGroup`
- `PrivateRDPSecurityGroup`

### Alarms