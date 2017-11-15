Codecommit FAWS Template
========================
codecommit.template - Creates an AWS CodeCommit repository. Please be aware that this template will create resources for which you will be charged.
### Parameters

#### Branches
- Default: `Master`
- Type: `CommaDelimitedList`
- Description: `Comma Delimited List of branch names. Maximum length 256`

#### CustomData
- Type: `String`
- ConstraintDescription: `Maximum length 1000.`
- Description: `Any custom data associated with the trigger that will be included in the information sent to the target of the trigger.`
- MaxLength: `1000`

#### RepositoryDescription
- Default: `Created with CloudFormation.`
- ConstraintDescription: `Maximum length 1000.`
- Type: `String`
- Description: `A detailed description for the AWS CodeCommit repository.`
- MaxLength: `1000`

#### DestinationArn
- Type: `String`
- Description: `The ARN of the resource that is the target for a trigger. Full ARN required.`

#### TriggerName
- Description: `A detailed description for the AWS CodeCommit repository.`
- Default: `TriggerName`
- Type: `String`
- AllowedPattern: `([A-Za-z0-9._-]+)`
- MaxLength: `100`
- ConstraintDescription: `The repo description must contain only letters, numbers,  periods (.), underscores (_), and dashes (-). Maximum length 100.`

#### RepositoryName
- Type: `String`
- Description: `A name for the AWS CodeCommit repository.`
- MinLength: `1`
- AllowedPattern: `([A-Za-z0-9._-]+)`
- MaxLength: `100`
- ConstraintDescription: `The repo name must contain only letters, numbers, periods (.), underscores (_), and dashes (-). Maximum length 100`

#### EnableTrigger1
- Default: `False`
- Type: `String`
- Description: `Defines the actions to take in response to events that occur in the repository.`
- AllowedValues: `['True', 'False']`

### Outputs
- `CloneHTTP`
- `CloneSSH`
- `RepoName`
- `RepoARN`

### Alarms