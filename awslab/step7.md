## Deploying the cloudformation template

1. Now we have validated all the cloudformation templates, it's time to start deploying these template.

2. Let start deploying the cloudformation by the below command.

	- `aws cloudformation deploy --stack-name iam-stack --capabilities CAPABILITY_NAMED_IAM --template-file ./iam.yaml`{{execute}}

	- `aws cloudformation deploy --stack-name dynamodb-stack --template-file ./dynamodb.yaml --parameter-overrides TableName=<TABLE_NAME>`{{execute}}

  	- `aws cloudformation deploy --stack-name s3-lambda-stack --template-file ./s3_lambda.yaml --parameter-overrides bucketname=<S3_BUCKET_NAME>`{{execute}}




	
