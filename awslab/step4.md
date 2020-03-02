1. Let's create our third cloudformation template.

	Filename - lambda.yaml
	Reason for creating this file - It will create a lambda function which will execute our logic to read json from s3 bucket and update its entry into the dynamodb table.
	
	You can create file either using vi editor in termial using this command `vi lambda.yaml`{{execute}} or by creating a new file in editor with lambda.yaml

2. After the file is created add the following data into it :

**
AWSTemplateFormatVersion: '2010-09-09'
Description: Lambda function
Resources:
  LambdaFunction: 
    Type: AWS::Lambda::Function
    Properties:
      FunctionName: deploy      
      Handler: index.lambda_handler
      Role: !ImportValue CommonRole
      Code:
        ZipFile: !Sub |
          import json
          import boto3
          s3_client = boto3.client('s3')
          dynamodb = boto3.resource('dynamodb')
          def lambda_handler(event, context):
            bucket = event['Records'][0]['s3']['bucket']['name']
            json_file_name = event['Records'][0]['s3']['object']['key']
            json_object = s3_client.get_object(Bucket=bucket,Key=json_file_name)
            jsonFileReader = json_object['Body'].read()
            jsonDict = json.loads(jsonFileReader)
            table = dynamodb.Table('employeetable')
            table.put_item(Item=jsonDict)
            return {
              'statusCode': 200,
              'body': json.dumps('Hello from Lambda!')
            }
      Runtime: python3.6

Outputs:
  LambdaFunctionArn:
    Value: !GetAtt LambdaFunction.Arn
    Export:
      Name: deploylambda
**
