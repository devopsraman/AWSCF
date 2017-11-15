Route53Healthcheck FAWS Template
================================
route53_healthcheck.template - Route53 HealthCheck Monitors. Must be deployed in us-east-1.
### Parameters

#### EnableRackspaceTicket
- Default: `False`
- Type: `String`
- Description: `Specifies whether alarms will generate Rackspace tickets`
- AllowedValues: `['False', 'True']`

#### SearchString
- Default: ``
- Type: `String`
- Description: `If the string appears in the response body, Amazon Route 53 considers the resource healthy.  Ignored for TCP domain protocols.`

#### MonitoredDomain
- Type: `String`
- Description: `Domain or IP to monitor DO NOT include protocol(HTTP(S)://) `

#### ResourcePath
- Default: `/`
- Type: `String`
- Description: `Specifies HTTP path to monitor.  The path can be any value which returns an HTTP status code of 2xx or 3xx when the endpoint is healthy.  Ignored for TCP DomainProtocol.`

#### DomainProtocol
- Default: `HTTP`
- Type: `String`
- Description: `Specifies the protocol of the domain.`
- AllowedValues: `['HTTP', 'HTTPS', 'TCP']`

#### RequestInterval
- Default: `30`
- MinValue: `10`
- Type: `Number`
- Description: `The number of seconds between the finish of one Route 53 health check request and the start of the next.`
- MaxValue: `30`

#### Port
- Default: `80`
- Type: `Number`
- Description: `Specifies the port number to monitor.`

### Outputs

### Alarms
#### DomainAlarmAction
- Description: Domain has failed, generating ticket.
- Metric: HealthCheckStatus
- Threshold: 1
- Actions: `{'Fn::If': ['RackspaceAlarmsEnabled', {'Fn::Sub': 'arn:aws:sns:${AWS::Region}:${AWS::AccountId}:rackspace-support-emergency'}, {'Ref': 'AWS::NoValue'}]}`
