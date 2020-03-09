## Validating the cloudformation template

1. Now we have created all the cloudformation templates, it's time to start validate these template , it they are syntactically correct or not.

2. Let start validating the cloudformation by the below command.

	- `aws cloudformation validate-template --template-body file://iam.yaml`{{execute}}

	- `aws cloudformation validate-template --template-body file://dynamodb.yaml`{{execute}}

	- `aws cloudformation validate-template --template-body file://s3_lambda.yaml`{{execute}}

	
