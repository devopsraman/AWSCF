CodeDeployApplication FAWS Template
===================================
code_deploy_application.template - Create a Code Deploy Application
### Parameters

#### EnableS3Bucket
- Default: `False`
- Type: `String`
- Description: `Specifies whether an S3 artifcat bucket should be created.`
- AllowedValues: `['False', 'True']`

#### Name
- Type: `String`
- Description: `Application Name`

### Outputs
- `Application`
- `ArtifactBucket`

### Alarms