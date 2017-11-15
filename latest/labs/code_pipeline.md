CodePipeline FAWS Template
==========================
code_pipeline.template - Create a Continuous Deployment Pipeline Skeleton. Read the docs: http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/continuous-delivery-codepipeline.html
### Parameters

#### Repository
- Type: `String`
- Description: `Name of the Github Repository.`

#### CodePipelineRoleManagedPolicyArns
- Default: ``
- Type: `String`
- Description: `A comma delimited list of IAM policy ARNs for the CodePipelineRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### OAuthToken
- Type: `String`
- NoEcho: `True`
- Description: `Github OAuthToken with correct access to Repository.`

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### Branch
- Type: `String`
- Description: `Git branch to use as the source for this pipeline`

#### NotificationTopic
- Type: `String`
- Description: `Full ARN of notification topic.`

#### Organization
- Type: `String`
- Description: `Name of Github organization the source repository belongs to.`

### Outputs

### Alarms