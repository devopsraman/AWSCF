SystemsManagerServiceRole FAWS Template
=======================================
systems_manager_service_role.template - Infrastructure Template for Systems Manager Service Role
### Parameters

#### EnableAutomation
- Default: `True`
- Type: `String`
- Description: `Specifies whether the Automation IAM role will be created.`
- AllowedValues: `['False', 'True']`

#### EnableMaintenanceWindow
- Default: `True`
- Type: `String`
- Description: `Specifies whether the Maintenance Window IAM role will be created.`
- AllowedValues: `['False', 'True']`

### Outputs
- `AutomationRoleARN`
- `MaintenanceWindowRoleName`
- `AutomationRoleName`
- `MaintenanceWindowRoleARN`
- `AutomationInstanceProfileName`
- `AutomationInstanceProfileARN`

### Alarms