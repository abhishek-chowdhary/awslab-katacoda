## Deploying the cloudformation template

1. Now we have validated all the cloudformation templates, it's time to start deploying these template.

2. Let start deploying the cloudformation by the below command.

	- `aws cloudformation deploy --stack-name iam-stack --template-file ./iam.yaml`{{execute}}

	- `aws cloudformation deploy --stack-name dynamodb-stack --template-file ./dynamodb.yaml`{{execute}}

	- `aws cloudformation deploy --stack-name lambda-stack --template-file ./lambda.yaml --capabilities CAPABILITY_NAMED_IAM`{{execute}}

   Before executing below line , create a variavle with name 'bucketname' and set it value. " bucketname=your-s3-bucket-name "

  	- `aws cloudformation deploy --stack-name s3_lambda_invoke-stack --template-file ./s3_lambda_invoke.yaml --capabilities CAPABILITY_NAMED_IAM --parameter-overrides ${bucketname}`{{execute}}




	
