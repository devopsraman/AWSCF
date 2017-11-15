EcsCdPipeline FAWS Template
===========================
ecs_cd_pipeline.template - Create a Continuous Deployment Pipeline for an ECS Service. Unsupported!!!!
### Parameters

#### ECSServiceParameterKey
- Type: `String`
- Description: `Bucket Key for the Service Template Parameters file.`

#### ECSServiceParameterBucket
- Type: `String`
- Description: `Valid Bucket name housing the Service CloudFormation Parameters file.`

#### Repository
- Type: `String`
- Description: `Name of the Github Repository.`

#### CodePipelineRoleManagedPolicyArns
- Default: ``
- Type: `String`
- Description: `A comma delimited list of IAM policy ARNs for the CodePipelineRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### ECSServiceKey
- Type: `String`
- Description: `Bucket Key for the ECS Service CloudFormation Template.`

#### OAuthToken
- Type: `String`
- NoEcho: `True`
- Description: `Github OAuthToken with correct access to Repository.`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### CodeBuildRoleManagedPolicyArns
- Default: ``
- Type: `String`
- Description: `A comma delimited list of IAM policy ARNs for the CodeBuildRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### Branch
- Type: `String`
- Description: `Git branch to use as the source for this pipeline`

#### Organization
- Type: `String`
- Description: `Name of Github organization the source repository belongs to.`

#### ECSServiceStack
- Type: `String`
- Description: `Name of the ECS Service Stack this pipeline deploys to.`

#### CloudFormationBuildRoleManagedPolicyArns
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A comma delimited list of IAM policy ARNs for the CloudFormationBuildRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### ECSServiceBucket
- Type: `String`
- Description: `Valid Bucket name housing the Service CloudFormation Template for this service.`

### Outputs

### Alarms