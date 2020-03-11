## Deploying the cloudformation template

1. Now we have validated all the cloudformation templates, it's time to start deploying these template.

2. Let start deploying the cloudformation by the below command.

	- `aws cloudformation deploy --stack-name iam-stack --capabilities CAPABILITY_NAMED_IAM --template-file ./iam.yaml`{{execute}}

	- `aws cloudformation deploy --stack-name dynamodb-stack --template-file ./dynamodb.yaml`{{execute}}

   Before executing below line , create a variavle with name 'bucketname' and set it value. " bucketname=your-s3-bucket-name "

  	- `aws cloudformation deploy --stack-name s3-lambda-stack --template-file ./s3_lambda.yaml --parameter-overrides bucketname=${bucketname}`{{execute}}




	
