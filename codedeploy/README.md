
# Continous Integration and Continous Delivery Rails application into Amazon Cloud.
*OS*: CentOS 7

*Tools*: TeamCity, AWS CodeDeploy, Ansible

*Environments*: Test, Production 

## Description
This article is not about why we have choosen these kind of tools.
The aim of this article is to share my experience. 

## What do we have?
1. Rails app repository - github.com. Detailed information -https://github.com
2. AWS account - existed. Detailed information - https://aws.amazon.com
3. TeamCity - installed. Detailed information - https://www.jetbrains.com/teamcity

## How it works
<img src="Scheme2.png" width="250">

## Configuring AWS
### Configuring IAM
#### Creating new Roles and Polices
##### Step 1. New policy.
Create new policy to grant access Temacity user to S3 bucket.
Go to Create Policy -> Create Your Own Policy

<img src="Policy_1.PNG" width="250">
There is a code of policy:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "s3:*",
            "Resource": [
                "arn:aws:s3:::_your_s3_bucket_"
            ]
        }
    ]
}
```

#### Creating new User for Teamcity
##### Step 1. New User.
http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html
##### Step 2. Access key.
For Teamcity configuration we need to have Access key. Let's create it. **Do not forget to copy it!**

http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html

##### Step 3. Assign Polices.
List Polices should be assigned:
* AmazonEC2FullAccess
* AWSCodeDeployDeployerAccess
* Your policy created in Step 1 (Creating new Roles and Polices)

### Configuring S3
#### Step 1

<img src="s3_1.PNG" width="250">

#### Step 2

<img src="s3_2.PNG" width="250">

#### Step 3

<img src="s3_3.PNG" width="250">

#### Step 4

<img src="s3_4.PNG" width="250">

#### Step 5

Let's grant permissions to user under which Temacity will work with Amazon to put application versions to bucket.
Got to Bucket -> Permissions -> Bucket Policy and add to Bucket policy editor this json:

### Configuring CodeDeploy

