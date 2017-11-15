
## Description

Rackspace Hosting - Sets up a Lambda Role and SNS topics in order to enable Ebs Snapshots Automatic Backups

#### Metadata

 * **Version**: v0.1.0

## Parameters

 * **S3Bucket** - S3Bucket where to find the Scripts to run as Lambda Functions
  * Default: `rslambda-backup`

## Resources

 * **CreateBackup** - `AWS::Lambda::Function`
 * **CreateBackupAlarm** - `AWS::CloudWatch::Alarm`
 * **LambdaExecutionRole** - `AWS::IAM::Role`
 * **RemoveBackup** - `AWS::Lambda::Function`
 * **RemoveBackupAlarm** - `AWS::CloudWatch::Alarm`