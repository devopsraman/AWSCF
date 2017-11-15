
## Description

Rackspace Hosting - Creates the necessary S3 bucket. Please be aware that this template will create resources for which you will be charged.

#### Metadata

 * **AWS::CloudFormation::Interface**: {u'ParameterGroups': [{u'Parameters': [u'BucketName', u'EnableLogging', u'Website', u'Versioning', u'LifeCycle', u'AccessControl', u'ServerSideEncryption'], u'Label': {u'default': u'Bucket Configuration'}}, {u'Parameters': [u'Prefix', u'ExpirationInDays', u'TransitionInDays'], u'Label': {u'default': u'LifeCycle Configuration'}}, {u'Parameters': [u'ErrorDocument', u'IndexDocument'], u'Label': {u'default': u'Website Configuration'}}, {u'Parameters': [u'DestinationBucketName', u'LogFilePrefix'], u'Label': {u'default': u'Logging Configuration'}}]}
 * **Version**: v0.1.0

## Parameters

 * **AccessControl** - Define ACL for Bucket
  * Default: `BucketOwnerFullControl`
  * Constraint: `Must be either AuthenticatedRead, AwsExecRead, BucketOwnerRead, BucketOwnerFullControl, LogDeliveryWrite, Private, PublicRead or PublicReadWrite.`
 * **BucketName** - The name of the bucket to use. Must be unique.
  * Constraint: `The bucket name must contain only lowercase letters, numbers, periods (.), and dashes (-).`
 * **DestinationBucketName** - Where to store logs
  * Default: ``
 * **EnableLogging** - Enable Logging
  * Default: `No`
  * Constraint: `Must be either Yes or No.`
 * **Environment** - Application environment for which this network is being created. e.g. Development/Production.
  * Default: `Development`
 * **ErrorDocument** - Name for Error Document file
  * Default: `error.html`
 * **ExpirationInDays** - Indicates after how many days we are deleting objects
  * Default: `30`
  * Constraint: `Must be a valid number between 1 and 999.`
 * **IndexDocument** - Name for Index Document file
  * Default: `index.html`
 * **LifeCycle** - Enable LifeCycle config
  * Default: `No`
  * Constraint: `Must be either Yes or No.`
 * **LogFilePrefix** - Prefix for all log object keys
  * Default: `logs/`
 * **Prefix** - Prefix for Glacier Name
  * Default: `glacier`
 * **ServerSideEncryption** - Enable Server Side Encryption
  * Default: `No`
  * Constraint: `Must be either Yes or No.`
 * **TransitionInDays** - Indicates after how many days we are moving objects
  * Default: `30`
  * Constraint: `Must be a valid number between 1 and 999.`
 * **Versioning** - Enable Versioning
  * Default: `No`
  * Constraint: `Must be either Yes or No.`
 * **Website** - Enable Website
  * Default: `No`
  * Constraint: `Must be either Yes or No.`

## Conditions

 * **Glacier** - `{u'Fn::Equals': [{u'Ref': u'LifeCycle'}, u'Yes']}`
 * **Logging** - `{u'Fn::Equals': [{u'Ref': u'EnableLogging'}, u'Yes']}`
 * **ServerSideEncryption** - `{u'Fn::Equals': [{u'Ref': u'ServerSideEncryption'}, u'Yes']}`
 * **Versioning** - `{u'Fn::Equals': [{u'Ref': u'Versioning'}, u'Yes']}`
 * **Website** - `{u'Fn::Equals': [{u'Ref': u'Website'}, u'Yes']}`

## Resources

 * **S3Bucket** - `AWS::S3::Bucket`
 * **S3BucketwithWebsitePolicy** - `AWS::S3::BucketPolicy`
 * **ServerSideEncryptionPolicy** - `AWS::S3::BucketPolicy`