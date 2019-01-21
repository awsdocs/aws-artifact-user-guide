# Getting Started with AWS Artifact<a name="getting-started"></a>

AWS Artifact offers a number of documents for downloading and allows you to accept and manage legal agreements such as the Business Associate Addendum \(BAA\)\. If you use AWS Organizations, you can accept agreements on behalf of all accounts within your organization\. When accepted, all existing and subsequent member accounts are automatically covered by the agreement\.

This Getting Started tutorial shows you how to set up permissions to download reports or manage agreements by completing the following steps:

1. [Step 1: Create an Administrators Group and Add an IAM User](#create-an-admin)

1. [Step 2: Download a Report and Manage an Agreement](#download-first-artifact)

## Step 1: Create an Administrators Group and Add an IAM User<a name="create-an-admin"></a>

In this step, you create an Administrators group, create an IAM user for yourself, and add your IAM user to the group\. Creating an IAM group allows you to attach the permissions to a group instead of an individual user, and you can grant the same permission to other users by adding them to the group\.

**To create an IAM user for yourself and add the user to an Administrators group**

1. Use your AWS account email address and password to sign in as the *[AWS account root user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html)* to the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.
**Note**  
We strongly recommend that you adhere to the best practice of using the **Administrator** IAM user below and securely lock away the root user credentials\. Sign in as the root user only to perform a few [account and service management tasks](https://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)\.

1. In the navigation pane of the console, choose **Users**, and then choose **Add user**\.

1. For **User name**, type **Administrator**\.

1. Select the check box next to **AWS Management Console access**, select **Custom password**, and then type the new user's password in the text box\. You can optionally select **Require password reset** to force the user to create a new password the next time the user signs in\.

1. Choose **Next: Permissions**\.

1. On the **Set permissions** page, choose **Add user to group**\.

1. Choose **Create group**\.

1. In the **Create group** dialog box, for **Group name** type **Administrators**\.

1. For **Filter policies**, select the check box for **AWS managed \- job function**\.

1. In the policy list, select the check box for **AdministratorAccess**\. Then choose **Create group**\.

1. Back in the list of groups, select the check box for your new group\. Choose **Refresh** if necessary to see the group in the list\.

1. Choose **Next: Tags** to add metadata to the user by attaching tags as key\-value pairs\.

1. Choose **Next: Review** to see the list of group memberships to be added to the new user\. When you are ready to proceed, choose **Create user**\.

You can use this same process to create more groups and users, and to give your users access to your AWS account resources\. To learn about using policies to restrict users' permissions to specific AWS resources, go to [Access Management](https://docs.aws.amazon.com/IAM/latest/UserGuide/access.html) and [Example Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_examples.html)\.

**Note**  
For information on IAM policies that are specific to AWS Artifact, see [Controlling Access](controlling-access.md)\.

You can repeat the preceding steps one through six and then choose the **Administrators** group from the list to grant administrator permissions to other IAM users\.

## Step 2: Download a Report and Manage an Agreement<a name="download-first-artifact"></a>

Now that you have set up your IAM users and policies, you can download a document by following the procedure in [Downloading Reports in AWS Artifact](downloading-documents.md)\. You can also manage your AWS agreements\. For more information, see [Managing Your Agreements in AWS Artifact](managingagreements.md)\. 