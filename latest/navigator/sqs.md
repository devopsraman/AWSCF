Sqs FAWS Template
=================
sqs.template - Creates the necessary SQS Queue. Please be aware that this template will create resources for which you will be charged.
### Parameters

#### SQSQueueName
- MinLength: `3`
- Type: `String`
- Description: `REQUIRED. The name of the SQS queue.`
- ConstraintDescription: `Must a string of at least 3 characters.`

#### RedrivePolicy
- Default: `False`
- Type: `String`
- Description: `OPTIONAL. Indicates whether this queue uses a dead letter queue.`
- AllowedValues: `['False', 'True']`

#### InternalRecordName
- Default: ``
- Type: `String`
- Description: `Record Name for the new Resource Record in the Internal Hosted Zone`

#### RoleARN
- AllowedPattern: `^arn:aws:iam::[0-9]+:role/.+$`
- ConstraintDescription: `Must match the pattern arn:aws:iam::[0-9]+:role/.+`
- Type: `String`
- Description: `REQUIRED. The EC2 Instance Role allowed to talk with the SQS queue.`

#### InternalZoneName
- Default: ``
- Type: `String`
- Description: `TLD for Internal Hosted Zone`

#### ContentBasedDeduplication
- Default: `False`
- Type: `String`
- Description: `OPTIONAL. For First-In-First-Out (FIFO) queues, specifies whether to enable content-based deduplication.`
- AllowedValues: `['False', 'True']`

#### FifoQueue
- Default: `False`
- Type: `String`
- Description: `OPTIONAL. Indicates whether this queue is a FIFO queue.`
- AllowedValues: `['False', 'True']`

#### InternalZoneId
- Default: ``
- Type: `String`
- Description: `The Route53 Internal Hosted Zone ID`

### Outputs
- `SQSQueueName`
- `SQSQueueARN`
- `SQSQueueURL`

### Alarms