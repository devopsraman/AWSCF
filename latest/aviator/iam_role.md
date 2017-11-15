IamRole FAWS Template
=====================
iam_role.template - Create an IAM Service Role
### Parameters

#### Services
- Type: `CommaDelimitedList`
- Description: `A comma delimited list of services endpoints that can assume this role.`

#### RoleName
- Default: ``
- Type: `String`
- Description: `The name to use for the IAM Role.  If omitted, a name will be generated for the role. OPTIONAL`

#### ServiceRoleManagedPolicyArns
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A comma delimited list of IAM policy ARNs for the ServiceRole IAM role.  IAM ARNs can be found within the Policies section of the AWS IAM console.`

### Outputs

### Alarms