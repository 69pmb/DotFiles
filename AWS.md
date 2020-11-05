## AWS
### SQS
- Send a message:  
`aws --endpoint-url=http://localhost:4576 
sqs send-message --queue-url http://localhost:4576/queue/eventQueue.fifo --message-group-id test --message-body "{\"action\":\"UPSERT\",\"hotelCode\":\"1131\",\"updateTime\":\"1575454982307\"}"`
- List queues:  
`aws --endpoint-url=http://localhost:4576 sqs list-queues`

### DynamoDb
- List tables:  
`aws --endpoint-url=http://localhost:4569 dynamodb list-tables`
- Query:  
`aws --endpoint-url=http://localhost:4569 dynamodb query --table-name PropertyDocument --key-condition-expression "#propertycodelang= :v1" --expression-attribute-values '{":v1":{"S":"1546-en"}}' --expression-attribute-names '{"#propertycodelang":"property_code-lang"}'`

### S3
- Creates a bucket:  
`aws --endpoint-url=http://localhost:4572 s3 mb s3://flowBucket`
- Sets the permissions:  
`aws s3api put-bucket-acl --bucket flowBucket --acl public-read --endpoint-url=http://localhost:4572`
- Lists buckets:  
`aws s3 ls --profile local --endpoint-url=http://localhost:4572`
- Upload a file:  
`aws s3 cp --acl public-read wco/WebXml.zip --endpoint-url=http://localhost:4572 s3://flowBucket`