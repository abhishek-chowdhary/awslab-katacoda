## Setting up the environment.....

1. Update the current packages and installing awscli using apt-get command
	
	`apt-get update`{{execute}}
	`curl https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip -o awscliv2.zip`{{execute}}        
	`unzip awscliv2.zip && sudo ./aws/install`{{execute}}
	`export PATH=$PATH:/usr/local/bin`{{execute}}
   
   Check the aws cli version :
       
       `aws --version`{{execute}}       

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
