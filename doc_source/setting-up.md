# Setting Up AWS Artifact<a name="setting-up"></a>

When you sign up for Amazon Web Services \(AWS\), your AWS account is automatically signed up for all services in AWS, including AWS Artifact\. If you haven't signed up for AWS, see [Sign Up for AWS](#setting-up-aws-sign-up)\. To create and manage user identity and permissions to provide highly secure, limited access to your AWS resources, both for yourself and for others who need to work with your AWS resources, see [Create an IAM User](#setting-up-create-iam-user)\. 


+ [Sign Up for AWS](#setting-up-aws-sign-up)
+ [Create an IAM User](#setting-up-create-iam-user)

## Sign Up for AWS<a name="setting-up-aws-sign-up"></a>

If you do not have an AWS account, use the following procedure to create one\.

**To sign up for AWS**

1. Open [https://aws\.amazon\.com/](https://aws.amazon.com/) and choose **Create an AWS Account**\.

1. Follow the online instructions\.

 Part of the sign\-up procedure involves receiving a phone call and entering a PIN using the phone keypad\. 

## Create an IAM User<a name="setting-up-create-iam-user"></a>

When you sign up for AWS, you provide an email address and password that is associated with your AWS account\. These are your *root credentials*, and they provide complete access to all of your AWS resources\. However, we strongly recommend that you don't use the root account for everyday access\. We also recommend that you don't share account credentials with others to give them complete access to your account\. 

Instead of logging in to the account with your root credentials or sharing your credentials with others, you should create a special user identity called an *IAM user* for yourself and for anyone who might need access to a document in AWS Artifact\. With this approach, you can provide individual sign\-in information for each user, and you can grant each user only the permissions that he or she needs to work with specific documents\. For more information, see [Step 1: Create an Admin Group and Add an IAM User](getting-started.md#create-an-admin)\.

If you already manage user identities outside of AWS, you can use IAM *identity providers* instead of creating IAM users in your AWS account\. For more information, see [Identity Providers and Federation](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers.html) in the *IAM User Guide*\.