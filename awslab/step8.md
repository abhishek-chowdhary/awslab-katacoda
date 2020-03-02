## Uploading json file to S3 bucket

1. Now we have are infrastructure up and ready. Let's test if it works fine.

2. Upload a json file in S3 bucket .

3. Then check the items tab inside dynamodb table , if it contains the data present in json file or not. 

4. If yes, everything works fine, If not , then check the cloudwatch logs for the lambda which was created by going to the cloudwatch and selecting log option from it. Then choose the log group which was created during lambda creation and check its latest log stream for the error.
