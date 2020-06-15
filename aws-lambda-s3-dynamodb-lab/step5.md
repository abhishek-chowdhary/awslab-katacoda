1. Let's create our last cloudformation template.

	- Filename - s3_lambda.yaml
	- Reason for creating this file - It will create a S3 bucket where we will upload our artifacts and also create a lambda invoke permission so that s3 event can trigger lambda function on file upload event.
	
   You can create file either using vi editor in termial using this command `vi s3_lambda.yaml`{{execute}} or by creating a new file in editor with s3_lambda.yaml

2. After the file is created add the following data into it :

```
AWSTemplateFormatVersion: '2010-09-09'
Description: Lambda function
Parameters:
  BucketName:
    Type: String
Resources:
  S3Bucket:
    Type: "AWS::S3::Bucket"
    Properties:
      BucketName: !Ref BucketName   #specify bucket name
      NotificationConfiguration:
        LambdaConfigurations:
          - Event: s3:ObjectCreated:*
            Function: !GetAtt LambdaFunction.Arn
            Filter:
              S3Key:
                Rules:
                - Name: suffix
                  Value: .json
    DependsOn:
     - LambdaInvoke

  LambdaFunction: 
    Type: AWS::Lambda::Function
    Properties:
      FunctionName: deploy       #specify lambda name
      Handler: index.lambda_handler
      Role: !ImportValue CommonRole  #specify role name
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
            table = dynamodb.Table('employeetable')     #specify table name
            table.put_item(Item=jsonDict)
            return {
              'statusCode': 200,
              'body': json.dumps('Success!')
            }
      Runtime: python3.6

  LambdaInvoke:
    Type: AWS::Lambda::Permission
    Properties: 
      Action: lambda:InvokeFunction
      FunctionName: !Ref LambdaFunction
      Principal: s3.amazonaws.com
      SourceAccount: !Ref 'AWS::AccountId'
      SourceArn: !Sub 'arn:aws:s3:::${BucketName}'
```
