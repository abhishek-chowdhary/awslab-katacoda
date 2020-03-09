1. Let's create our second cloudformation template.

	- Filename - dynamodb.yaml
	- Reason for creating this file - It will create a dynamodb table.
	
    You can create file either using vi editor in termial using this command `vi dynamodb.yaml`{{execute}} or by creating a new file in editor with dynamodb.yaml

2. After the file is created add the following data into it :

```
AWSTemplateFormatVersion: "2010-09-09"
Description: DynamoDb table 
Parameters:
  TableName: 
    Type: String 
Resources:
  Employeetable: 
    Type: AWS::DynamoDB::Table
    Properties:
      TableName: employeetable    #specify table name
      AttributeDefinitions: 
        - AttributeName: "empid"
          AttributeType: "S"
      KeySchema:
        - AttributeName: "empid"
          KeyType: "HASH"
      ProvisionedThroughput: 
        ReadCapacityUnits: 5
        WriteCapacityUnits: 5
```
