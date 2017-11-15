IamUserGroup FAWS Template
==========================
iam_user_group.template - Creates IAM Users and an associated group
### Parameters

#### UserName1
- Default: ``
- Type: `String`
- Description: `The name to use for User 1. OPTIONAL`

#### UserName3
- Default: ``
- Type: `String`
- Description: `The name to use for User 3. OPTIONAL`

#### UserName2
- Default: ``
- Type: `String`
- Description: `The name to use for User 2. OPTIONAL`

#### UserName5
- Default: ``
- Type: `String`
- Description: `The name to use for User 5. OPTIONAL`

#### UserName4
- Default: ``
- Type: `String`
- Description: `The name to use for User 4. OPTIONAL`

#### ExistingGroupNames
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A comma delimited list of existing IAM groups that should be assigned to all users created in this template.  If this parameter is set, no new group will be created.  (OPTIONAL)`

#### ManagedPolicies
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A comma delimited list of IAM policy ARNs for the IAM group.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

#### NewGroupName
- Default: ``
- Type: `String`
- Description: `The name to use for the new IAM Group.  If omitted, a name will be generated for the new group.  Unused if Existing Groups are supplied. OPTIONAL`

### Outputs
- `IamGroup`

### Alarms