1. Let's create our last cloudformation template.

	- Filename - s3_lambda_invoke.yaml
	- Reason for creating this file - It will create a S3 bucket where we will upload our artifacts and also create a lambda invoke permission so that s3 event can trigger lambda function on file upload event.
	
   You can create file either using vi editor in termial using this command `vi s3_lambda_invoke.yaml`{{execute}} or by creating a new file in editor with s3_lambda_invoke.yaml

2. After the file is created add the following data into it :

```
AWSTemplateFormatVersion: "2010-09-09"
Description: S3 bucket 
Parameters:
  BucketName: 
    Type: String 
Resources:
  S3Bucket: 
    Type: "AWS::S3::Bucket"
    Properties:
      BucketName: !Ref BucketName
      NotificationConfiguration:
        LambdaConfigurations:
          - Event: s3:ObjectCreated:*
            Function: !GetAtt deploylambda
            Filter:
              S3Key:
                Rules:
                - Name: suffix
                  Value: .json
  LambdaInvoke:
    Type: AWS::Lambda::Permission
    Properties: 
      Action: lambda:InvokeFunction
      FunctionName: !Ref LambdaFunction
      Principal: s3.amazonaws.com
      SourceAccount: !Ref 'AWS::AccountId'
      SourceArn: !ImportValue S3Bucket 
Outputs:
  S3BucketArn:  
    Value: !GetAtt S3Bucket.Arn 
    Export:
      Name: S3Bucket                    #specify bucket export name
```
