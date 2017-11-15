RdsEventSubscriptions FAWS Template
===================================
rds_event_subscriptions.template - Creates an RDS Event Subscription.
### Parameters

#### SourceIds
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A list of Source IDs.  Submissions will be made to the provided NotificationTopic for each matching source ID. Acceptable values cary depending on the SourceType selected or omitted for all events.  Parameter ignored if SourceType is set to all. (OPTIONAL)`

#### EventCategories
- Default: ``
- Type: `CommaDelimitedList`
- Description: `A list of RDS event categories.  Submissions will be made to the provided NotificationTopic for each matching event. Acceptable values can be found with the CLI command 'aws rds describe-event-categories' or omitted for all events.  Parameter ignored if SourceType is set to all. (OPTIONAL)`

#### SourceType
- Default: `all`
- Type: `String`
- Description: `The type of source for which Amazon RDS provides notification events..`
- AllowedValues: `['all', 'db-instance', 'db-security-group', 'db-parameter-group', 'db-snapshot', 'db-cluster', 'db-cluster-snapshot']`

#### NotificationTopic
- AllowedPattern: `^arn:aws:sns:(us|eu|ap|sa|ca)-(east|west|north|south|southeast|northeast|central)-[1-9]:[0-9]+:.+$`
- ConstraintDescription: `Must match the pattern arn:aws:sns:(us|eu|ap|sa|ca)-(east|west|north|south|southeast|northeast|central)-[1-9]:[0-9]+:.+`
- Type: `String`
- Description: `SNS Topic ARN to notify if there are any alarms. (OPTIONAL)`

### Outputs

### Alarms