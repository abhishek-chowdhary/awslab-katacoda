##Setting up the environment.....

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
	
	`aws s3 ls`{{execute}}

   - It will list the s3 bucket present in the account.

4. Cloning the awslab material git repository .

	`git clone https://github.com/abhishek-chowdhary/awslab.git`{{execute}}
