
## Description

AWS CloudFormation Sample Template ElasticBeanstalk_PHP_Sample: Configure and launch the AWS Elastic Beanstalk sample application. **WARNING** This template creates one or more Amazon EC2 instances. You will be billed for the AWS resources used if you create a stack from this template.

## Parameters

 * **AppSubnet** - Subnets for Application
 * **ApplicationName** - (Optional) Specify the name of the Elastic Beanstalk Application. Must be unique on the account.
  * Default: ``
 * **DBSubnet** - Subnets for AWS RDS instance as part of application
 * **ELBSubnet** - Subnets for Elastic Loadbalancer
 * **ELBType** - Should Loadbalancer be internal only. No Internet Access
  * Default: `False`
 * **InstanceTypeParameter** - Enter t2.micro, m1.small, or m1.large. Default is t2.micro.
  * Default: `t2.micro`
 * **InstancesPublicIP** - Specifies whether to launch instances with public IP addresses in your VPC
  * Default: `False`
 * **KeyName** - Name of an existing EC2 KeyPair to enable SSH access to the AWS Elastic Beanstalk instance
  * Constraint: `Must be the name of an existing EC2 KeyPair.`
 * **VPCID** - Select Virtual Private Cloud ID

## Conditions

 * **SetApplicationName** - `{u'Fn::Equals': [{u'Ref': u'ApplicationName'}, u'']}`

## Mappings

 * **Region2Principal**:
  * `(u'us-east-1', {u'EC2Principal': u'ec2.amazonaws.com', u'OpsWorksPrincipal': u'opsworks.amazonaws.com'})`
  * `(u'cn-north-1', {u'EC2Principal': u'ec2.amazonaws.com.cn', u'OpsWorksPrincipal': u'opsworks.amazonaws.com.cn'})`
  * `(u'ap-northeast-1', {u'EC2Principal': u'ec2.amazonaws.com', u'OpsWorksPrincipal': u'opsworks.amazonaws.com'})`
  * `(u'sa-east-1', {u'EC2Principal': u'ec2.amazonaws.com', u'OpsWorksPrincipal': u'opsworks.amazonaws.com'})`
  * `(u'ap-southeast-1', {u'EC2Principal': u'ec2.amazonaws.com', u'OpsWorksPrincipal': u'opsworks.amazonaws.com'})`
  * `(u'ap-southeast-2', {u'EC2Principal': u'ec2.amazonaws.com', u'OpsWorksPrincipal': u'opsworks.amazonaws.com'})`
  * `(u'us-west-2', {u'EC2Principal': u'ec2.amazonaws.com', u'OpsWorksPrincipal': u'opsworks.amazonaws.com'})`
  * `(u'us-west-1', {u'EC2Principal': u'ec2.amazonaws.com', u'OpsWorksPrincipal': u'opsworks.amazonaws.com'})`
  * `(u'eu-central-1', {u'EC2Principal': u'ec2.amazonaws.com', u'OpsWorksPrincipal': u'opsworks.amazonaws.com'})`
  * `(u'eu-west-1', {u'EC2Principal': u'ec2.amazonaws.com', u'OpsWorksPrincipal': u'opsworks.amazonaws.com'})`

## Resources

 * **Application** - `AWS::ElasticBeanstalk::Application`
 * **ApplicationVersion** - `AWS::ElasticBeanstalk::ApplicationVersion`
 * **ConfigurationTemplate** - `AWS::ElasticBeanstalk::ConfigurationTemplate`
 * **Environment** - `AWS::ElasticBeanstalk::Environment`
 * **WebServerInstanceProfile** - `AWS::IAM::InstanceProfile`
 * **WebServerRole** - `AWS::IAM::Role`
 * **WebServerRolePolicy** - `AWS::IAM::Policy`

## Outputs

 * **URL** - `{u'Fn::Join': [u'', [u'http://', {u'Fn::GetAtt': [u'Environment', u'EndpointURL']}]]}`