## Uploading json file to S3 bucket

1. Now we have are infrastructure up and ready. Let's test if it works fine.

2. Create a demo.json file `vi demo.json`{{execute}} and put the following content in it :
   '''
    {
       "empid":"2",
       "name":"Peter",
       "age":22 
    }
   '''
   
   Upload a json file to S3 bucket created using following command.
   
    `aws s3 cp demo.json s3://<BUCKET_NAME>`{{execute}}

3. Then check the items tab inside dynamodb table , if it contains the data that was present in json file or not. 

4. If yes, everything works fine, if not, then check the cloudwatch logs for the lambda which was created by going to the cloudwatch and selecting log option from it. Then choose the log group which was created during lambda creation and check its latest log stream for the error.
