## Create a S3 Policy File and Use It to Modify Bucket Policy

- Create a policy_s3.json using following command or editor.   `vi policy_s3.json`
- Enter the following content in it:
  
  '''
        {
          "Version": "2012-10-17",
          "Statement": [
           {
            "Effect": "Allow",
            "Action": "s3:GetObject",
            "Principal": "*",
            "Resource": "arn:aws:s3:::<REPLACE-WITH-BUCKET-NAME>/*"
           },
           {
            "Effect": "Allow",
            "Action": "s3:ListBucket",
            "Principal": "*",
            "Resource": "arn:aws:s3:::<REPLACE-WITH-BUCKET-NAME>"
           }
          ]
        }

    '''

- Replace "REPLACE-WITH-BUCKET-NAME" with the bucketname. Save and exit the file.
- S3 policy file will modify the bucket policy so your objects are publicly accessible. Run the following command:
	`aws s3api put-bucket-policy --bucket <UNIQUE_BUCKET_NAME> --policy file://policy_s3.json`{{execute}}

## Create a Basic `index.html` Page and Upload File

- Create a basic HTML page:

    `echo "<html><center><h1>My Static Website on S3</h1></center></html>" > index.html`{{execute}}

- Upload the index.html file to your S3 website bucket using the AWS S3 API CLI:

    `aws s3 cp index.html s3://<UNIQUE_BUCKET_NAME>`{{execute}}


## Verify Your S3 Static Website Is Working

- Enter the S3 website URL for your bucket in the browser to ensure it's working.

    `curl http://<UNIQUE_BUCKET_NAME>.s3-website.us-east-1.amazonaws.com`{{execute}}
