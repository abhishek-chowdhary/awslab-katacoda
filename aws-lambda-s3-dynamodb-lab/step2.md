1. Now, we have cloned the repository. Let's create a new directory inside the cloned repository .

	`mkdir infrastructure; cd infrastructure`{{execute}}

2. What all we will be creating as a part of this exercise:

	- iam.yaml
	- dynamodb.yaml
	- s3_lambda.yaml

3. Let's create our first cloudformation template.

	- Filename - iam.yaml
	- Reason for creating this file - It will create a IAM role which will have the following policy attach to it : S3,Cloudwatch logs,DynamoDB
	
   You can create file either using vi editor in termial using this command `vi iam.yaml`{{execute}} or by creating a new file in editor with iam.yaml

4. After the file is created add the following data into it :

```
AWSTemplateFormatVersion: "2010-09-09"
Description: Role and Policy
Resources:
  CommonRole:
    Type: AWS::IAM::Role
    Properties:
      RoleName: commonrole          #specify role name
      AssumeRolePolicyDocument:
        Version: 2012-10-17
        Statement:
          - Effect: Allow
            Principal:
              Service:
              - lambda.amazonaws.com
            Action:
              - 'sts:AssumeRole'
      Policies: 
        - PolicyName: commonPolicy   #specify policy anme
          PolicyDocument:
            Version: 2012-10-17
            Statement:
              - Effect: Allow
                Action:
                  - 'dynamodb:*'
                  - 's3:*'
                  - 'logs:*'
                Resource: '*'
Outputs:
  CommonRoleArn:  
    Value: !GetAtt CommonRole.Arn 
    Export:
      Name: CommonRole               #specify export name
```
