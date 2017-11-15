
## Description

Rackspace Hosting - Create an EFS Filesystem with 2AZ's and Mount Points

#### Metadata

 * **LastUpdated**: 2016-06-28
 * **Version**: v0.1.0

## Parameters

 * **EFSSecurityGroupList** - Security Group List assigned to the EFS FileSystem
 * **Environment** - Application environment for which this EFS is being created. e.g. Development/Production
  * Default: `Development`
 * **SubnetAZ1** - Private Subnet for AZ1 EFS Mount Point
 * **SubnetAZ2** - Private Subnet for AZ2 EFS Mount Point
 * **VPCID** - Select Virtual Private Cloud ID
 * **VolumeName** - The name to be used for the EFS volume
  * Default: `myEFSvolume`

## Resources

 * **MountTargetAZ1** - `AWS::EFS::MountTarget`
 * **MountTargetAZ2** - `AWS::EFS::MountTarget`
 * **WebServerFileSystem** - `AWS::EFS::FileSystem`

## Outputs

 * **outputFileSystemID** - `{u'Ref': u'WebServerFileSystem'}`
 * **outputMountTargetIDAZ1** - `{u'Ref': u'MountTargetAZ1'}`
 * **outputMountTargetIDAZ2** - `{u'Ref': u'MountTargetAZ2'}`