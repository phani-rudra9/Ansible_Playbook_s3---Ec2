# Ansible_Playbook_s3-->Ec2
Deploying jenkins artifact from AWS S3 to AWS EC2

To work with this module you need to have on the remote server which you want to access

--> boto

--> boto3

--> botocore

--> python>= 2.6

Create a IAM role for EC2-->S3 and attach the IAM role the remote server 


  ### Setup steps 
1. Create a S3 bucket to store artifacts  
    `S3 --> Create bucket `
      ```sh 
   Bucket name: jenkins-s3-artifact 
   Region: Mumbai
   ```
1. Create new IAM role with "S3 full access" and assign it to jenkins server  
   `IAM --> Create role --> EC2` 
   ```ssh 
   Permission: AmazonS3FullAccess 
   Tags: key - Name, Value - S3FullAccess Role 
   name: S3_Full_Access
   ```
   
1. Install "S3 Publisher" plugin on Jenkins  
  `Manage Jenkins --> Manage Plugins --> Availabe --> S3 publisher`

1. Configure S3 profile on Jenkins  
  `Manage Jenkins --> Configure Systems --> Amazon S3 profiles` 
   ```sh
   Profile name : s3-artifact-repository 
   Use IAM Role : chose
   ```

1. Create a job to store artifacts under S3.
