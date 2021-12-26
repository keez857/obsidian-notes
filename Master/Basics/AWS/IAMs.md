### IAM Access keys

Consist of **Access Key ID** and the **Secret Access Key. **

**Access Key IDs**
Always begin with the letters **AKIA** and are 20 characters long. These act as a user name for the AWS API.  

**The Secret Access Key**
40 characters long. AWS generates both strings; however, AWS doesn't make the Secret Access Key available to download after the initial generation. 

---

### Short Term Creds

There is another type of credentials, short-term credentials, where the Access Key ID begins with the letters **ASIA** and includes an additional string called the Session Token. 
Conducting Reconnaissance with IAM

---

When you find credentials to AWS, you can add them to your AWS Profile in the AWS CLI. For this, you use the command:

`aws configure --profile PROFILENAME`

This command will add entries to the .aws/config and .aws/credentials files in your user's home directory. 

Once you have configured a new profile with the new access keys, you can execute any command using this other set of credentials. For example, to list all the S3 Buckets in the AWS account you have found credentials for, try:

`aws s3 ls --profile PROFILENAME`

ProTip: Never store a set of access keys in the [default] profile. Doing so forces you always to specify a profile and never accidentally run a command against an account you don't intend to. 

---

### Recon Techniques

A few other common AWS reconnaissance techniques are:

   1) Finding the Account ID belonging to an access key:
	       `aws sts get-access-key-info --access-key-id AKIAEXAMPLE --profile PROFILENAME`
   2) Determining the Username the access key you're using belongs to
	   `aws sts get-caller-identity --profile PROFILENAME`
   3) Listing all the EC2 instances running in an account
	   `aws ec2 describe-instances --output text --profile PROFILENAME`
   4) Listing all the EC2 instances running in an account in a different region
	   `aws ec2 describe-instances --output text --region us-east-1 --profile PROFILENAME`

---

### Secrets manager

`aws secretsmanager list-secrets --profile PROFILENAME`
Secret ID will usually be the "Name" value

`aws secretsmanager get-secret-value --secret-id SECRETID --profile PROFILENAME`