S3fs FAWS Template
==================
s3fs.template - Creates the necessary S3 bucket, IAM Role, and IAM Instance Profile for using the s3fs-fuse mount. Additional steps are required to use this template. Please be aware that this template will create resources for which you will be charged.
### Parameters

#### Environment
- Default: `Development`
- Type: `String`
- Description: `Application environment for which this network is being created. e.g. Development/Production.`
- AllowedValues: `['Development', 'Integration', 'PreProduction', 'Production', 'Staging', 'Test']`

#### BucketName
- AllowedPattern: `([a-z0-9\.-]+)`
- ConstraintDescription: `The bucket name must contain only lowercase letters, numbers, periods (.), and dashes (-).`
- Type: `String`
- Description: `The name of the bucket to use for the s3fs-fuse mount. Must be unique.`

#### Versioning
- Default: `Enabled`
- Type: `String`
- Description: `Enable versioning for the S3 bucket.`
- AllowedValues: `['Enabled', 'Suspended']`

#### IAMRoleS3FSManagedPolicyArns
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A comma delimited list of IAM policy ARNs for the IAMRoleS3FS IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

### Outputs
- `IAMRole`
- `MountCommand`
- `InstanceProfile`
- `Bucket`

### Alarms