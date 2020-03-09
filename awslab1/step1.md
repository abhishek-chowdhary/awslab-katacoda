## Setting up the environment.....

1. Update the current packages and installing awscli using apt-get command
	
	`apt-get update`{{execute}}
	`apt-get install awscli -y`{{execute}}

2. Configuring the aws cli

	`aws configure`{{execute}}

   Please enter the following details

  -	AWS Access Key ID [None]:
  -	AWS Secret Access Key [None]:
  -	Default region name [None]:
  -	Default output format [None]:

3. After configuring the awscli , please validate if its working fine by running the following command :
	
	`aws --version && aws s3 ls`{{execute}}

   - It will list the aws cli version and the s3 bucket present in the account.
