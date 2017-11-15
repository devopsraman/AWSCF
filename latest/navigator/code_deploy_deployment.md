CodeDeployDeployment FAWS Template
==================================
code_deploy_deployment.template - Create a Code Deploy Deployment
### Parameters

#### ApplicationName
- Type: `String`
- Description: `Application Name`

#### AutoScalingGroups
- Default: `none`
- Type: `CommaDelimitedList`
- Description: `Autoscaling Groups. Ex: 'asg1, asg2'`

#### EC2TagKey
- Default: ``
- Type: `String`
- Description: `Tag Key for EC2 Tag Filter (Required when EC2TagValue is Set)`

#### EnableS3Bucket
- Default: `False`
- Type: `String`
- Description: `Specifies whether an S3 artifcat bucket should be created.`
- AllowedValues: `['False', 'True']`

#### ServiceRoleManagedPolicyArns
- Default: ``
- Type: `String`
- Description: `A comma delimited list of IAM policy ARNs for the ServiceRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### EC2TagValue
- Default: ``
- Type: `String`
- Description: `Tag Value for ec2 Tag Filter (Required when EC2TagKey is Set)`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### DeploymentConfiguration
- Default: `CodeDeployDefault.OneAtATime`
- Type: `String`
- Description: `Code Deployment Configuration`
- AllowedValues: `['CodeDeployDefault.HalfAtATime', 'CodeDeployDefault.AllAtOnce', 'CodeDeployDefault.OneAtATime']`

### Outputs
- `DeploymentGroup`
- `ConfigurationBucket`

### Alarms