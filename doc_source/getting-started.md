# Getting Started<a name="getting-started"></a>

AWS Artifact offers a number of documents for downloading\. Different documents may require you to delegate permissions differently for various user accounts\. Permissions are delegated by using a combination of IAM policies and whitelisting\. This Getting Started section shows you how to set up permissions and download reports by completing the following steps:

1. [Step 1: Create an Admin Group and Add an IAM User](#create-an-admin)

1. [Step 2: Create an IAM Policy](#create-iam-policy)

1. [Step 3: Create IAM Users](#create-iam-user)

1. [Step 4: Download a Document](#download-first-artifact)

## Step 1: Create an Admin Group and Add an IAM User<a name="create-an-admin"></a>

In this step, you create an Administrators group and add yourself as an IAM user to the group\.

**To create an IAM user for yourself and add the user to an Administrators group**

1. Use your AWS account email address and password to sign in to the [AWS Management Console](https://console.aws.amazon.com/) as the *[AWS account root user](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html)*\.

1. In the navigation pane of the console, choose **Users**, and then choose **Add user**\.

1. For **User name**, type ** Administrator**\.

1. Select the check box next to **AWS Management Console access**, select **Custom password**, and then type the new user's password in the text box\. You can optionally select **Require password reset** to force the user to select a new password the next time the user signs in\.

1. Choose **Next: Permissions**\.

1. On the **Set permissions for user** page, choose **Add user to group**\.

1. Choose **Create group**\.

1. In the **Create group** dialog box, type ** Administrators**\.

1. For **Filter**, choose **Job function**\.

1. In the policy list, select the check box for ** AdministratorAccess**\. Then choose **Create group**\.

1. Back in the list of groups, select the check box for your new group\. Choose **Refresh** if necessary to see the group in the list\.

1. Choose **Next: Review** to see the list of group memberships to be added to the new user\. When you are ready to proceed, choose **Create user**\.

You can use this same process to create more groups and users, and to give your users access to your AWS account resources\. To learn about using policies to restrict users' permissions to specific AWS resources, go to [Access Management](http://docs.aws.amazon.com/IAM/latest/UserGuide/access.html) and [Example Policies](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_examples.html)\.

You can repeat the preceding steps to add other IAM users to the admin group\.

## Step 2: Create an IAM Policy<a name="create-iam-policy"></a>

In this step, you create a permissions policy that grants permissions to the IAM users in the group so they can access the AWS Artifact documents\. The following table shows the permissions that you can assign to IAM users based on the level of access that they need\. 


****  

| **Permissions Type** | **IAM Policy Document** | 
| --- | --- | 
| Permissions to Download All Reports |  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "artifact:Get"
            ],
            "Resource": [
                "arn:aws:artifact:::report-package/*"
            ]
        }
    ]
}
```  | 
|  **Permissions to Download All Agreements**  |  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "artifact:DownloadAgreement"
            ],
            "Resource": [
                "*"
            ]
        }
    ]
}
```  | 
| Permissions to Accept Agreements |  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "artifact:AcceptAgreement"
            ],
            "Resource": [
                "*"
            ]
        }
    ]
}
```  | 
| Permissions to Terminate Agreements |  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "artifact:TerminateAgreement"
            ],
            "Resource": [
                "*"
            ]
        }
    ]
}
```  | 

**To create an IAM policy**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\.

1. Choose **Create Policy**\.

1. Choose **Create Your Own Policy**\.

1. For **Policy Name**, type a unique name that helps you to remember what your policy is intended to do\.

1. For **Description**, type a description for your policy\.

1. For **Policy Document**, copy and paste one of the policy documents from the previous table, or copy and paste the following policy to grant access to ISO certiﬁcation reports, PCI compliance reports, and Service Organization Control \(SOC\) reports:

   ```
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Effect": "Allow",
               "Action": [
                   "artifact:Get"
               ],
               "Resource": [
                   "arn:aws:artifact:::report-package/Certifications and Attestations/SOC/*",
                   "arn:aws:artifact:::report-package/Certifications and Attestations/PCI/*",
                   "arn:aws:artifact:::report-package/Certifications and Attestations/ISO/*"
               ]
           }
       ]
   }
   ```

   To remove permissions for a specific type of report, remove the line with that report type\. For example, to remove the SOC reports, remove the following line:

   ```
   "arn:aws:artifact:::report-package/Certifications and Attestations/SOC/*",
   ```

1. Choose **Validate Policy**\. 

1. Choose **Create Policy**\.

Now that you have created your policy, you can attach the policy to a non\-admin group\.

## Step 3: Create IAM Users<a name="create-iam-user"></a>

In the preceding steps, you created an admin group, added yourself to the group as an IAM user, and created a permissions policy\. You can add other IAM users to the group at any time\. You also can create non\-admin groups and add IAM users to those groups\. Now that you have created an admin user and a policy, create a group of IAM users and add each of the people that you want to have access to AWS Artifact documents\. To do so, use the procedure from [Step 1: Create an Admin Group and Add an IAM User](#create-an-admin), using the policy that you just created in step two instead of **AdministratorAccess**\. 

## Step 4: Download a Document<a name="download-first-artifact"></a>

Now that you have set up your IAM users and policies, you can download a document by following the procedure in [Downloading Documents](downloading-documents.md)\.