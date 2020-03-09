## Modify Provided S3 Policy File and Use It to Modify Bucket Policy

- Open policy_s3.json using vi/vim.

- Put in the name of your bucket.
- Save and exit the file.
- Use the S3 policy file to modify the bucket policy so your objects are publicly accessible, which is a requirement for S3 static websites:


## Create a Basic `index.html` Page and Upload File


- Create a basic HTML page:

  `echo "<html><center><h1>My Static Website on S3</h1></center></html>" > index.html`{{execute}}

- Upload the index.html file to your S3 website bucket using the AWS S3 API CLI:

  `aws s3 cp index.html s3://<UNIQUE_BUCKET_NAME>`{{execute}}

## Verify Your S3 Static Website Is Working

- Enter the S3 website URL for your bucket in the browser to ensure it's working.

   `curl http://<UNIQUE_BUCKET_NAME>.s3-website.us-east-1.amazonaws.com`{{execute}}
