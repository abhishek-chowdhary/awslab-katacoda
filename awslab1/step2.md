## Create an S3 Bucket from AWS CLI


Create an S3 bucket in the us-east-1 region, giving your bucket a globally unique name, using the S3 API
  
  `aws s3api create-bucket --bucket <UNIQUE_BUCKET_NAME> --acl public-read`{{execute}}


## Modify the Newly Created Bucket to Be an S3 Website Bucket

Issue the AWS S3 API CLI command to enable the "Static website hosting" property of your bucket. In this same command, you'll also provide the index.html page, which iswhat your bucket URL will serve:


   `aws s3 website s3://<UNIQUE_BUCKET_NAME> --index-document index.html`

