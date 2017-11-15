SnsTopicSubscriptions FAWS Template
===================================
sns_topic_subscriptions.template - SNS Template. Creates a Topic with up to 3 Subscription.
### Parameters

#### SubscriptionEndpoint1
- Default: ``
- Type: `String`
- Description: `The subscription's endpoint #1.`

#### SubscriptionEndpoint3
- Default: ``
- Type: `String`
- Description: `The subscription's endpoint #3.`

#### SubscriptionEndpoint2
- Default: ``
- Type: `String`
- Description: `The subscription's endpoint #2.`

#### SubscriptionProtocol1
- Default: `http`
- Type: `String`
- Description: `The protocol you want to use in your endpoint #1. Supported protocols include: http, https, email, email-json, sms, sqs, application, lambda.`
- AllowedValues: `['http', 'https', 'email', 'email-json', 'sms', 'sqs', 'application', 'lambda']`

#### SubscriptionProtocol2
- Default: `http`
- Type: `String`
- Description: `The protocol you want to use in your endpoint #2. Supported protocols include: http, https, email, email-json, sms, sqs, application, lambda.`
- AllowedValues: `['http', 'https', 'email', 'email-json', 'sms', 'sqs', 'application', 'lambda']`

#### SubscriptionProtocol3
- Default: `http`
- Type: `String`
- Description: `The protocol you want to use in your endpoint #3. Supported protocols include: http, https, email, email-json, sms, sqs, application, lambda.`
- AllowedValues: `['http', 'https', 'email', 'email-json', 'sms', 'sqs', 'application', 'lambda']`

#### DisplayName
- Default: `MySNSTopic`
- Type: `String`
- Description: `A developer-defined string that can be used to identify this SNS topic.`

### Outputs
- `MySNSTopicTopicARN`

### Alarms