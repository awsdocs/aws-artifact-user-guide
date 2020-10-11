# Identity and access management in AWS Artifact<a name="security-iam"></a>

When you sign up for AWS, you provide an email address and password that are associated with your AWS account\. These are your *root credentials*, and they provide complete access to all of your AWS resources, including resources for AWS Artifact\. However, we strongly recommend that you don't use the root account for everyday access\. We also recommend that you don't share account credentials with others to give them complete access to your account\.

Instead of signing in to your AWS account with root credentials or sharing your credentials with others, you should create a special user identity called an *IAM user* for yourself and for anyone who might need access to a document or agreement in AWS Artifact\. With this approach, you can provide individual sign\-in information for each user, and you can grant each user only the permissions that they need to work with specific documents\. You can also grant multiple IAM users the same permissions by granting the permissions to an IAM group and adding the IAM users to the group\.

If you already manage user identities outside AWS, you can use IAM *identity providers* instead of creating IAM users\. For more information, see [Identity providers and federation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers.html) in the *IAM User Guide*\.

## Create IAM users and grant them access to AWS Artifact<a name="grant-access"></a>

Complete the following steps to grant users permissions to AWS Artifact based on the level of access they need\.

**Topics**
+ [Step 1: Create an IAM policy](#create-iam-policy)
+ [Step 2: Create an IAM group and attach the policy](#create-iam-group)
+ [Step 3: Create IAM users and add them to the group](#create-iam-user)

### Step 1: Create an IAM policy<a name="create-iam-policy"></a>

As an IAM administrator, you can create a policy that grants permissions to AWS Artifact actions and resources\.<a name="create-iam-policy-proc"></a>

**To create an IAM policy**

Use the following procedure to create an IAM policy that you can use to grant permissions to your IAM users and groups\.

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\.

1. Choose **Create policy**\.

1. Choose the **JSON** tab\.

1. Enter a policy document\. You can create you own policy, or you can use one of the policies from [Example IAM policies](#example-iam-policies)\.

1. Choose **Review Policy**\. The policy validator reports any syntax errors\.

1. On the **Review policy** page, enter a unique name that helps you remember the purpose of the policy\. You can also provide a description\.

1. Choose **Create policy**\.

### Step 2: Create an IAM group and attach the policy<a name="create-iam-group"></a>

As an IAM administrator, you can create a group and attach the policy that you created to the group\. You can add IAM users to the group at any time\.

**To create an IAM group and attach your policy**

1. In the navigation pane, choose **Groups** and then choose **Create New Group**\.

1. For **Group Name**, enter a name for your group and then choose **Next Step**\.

1. In the search field, enter the name of the policy that you created\. Select the check box for your policy and then choose **Next Step**\.

1. Review the group name and policies\. When you are ready, choose **Create Group**\.

### Step 3: Create IAM users and add them to the group<a name="create-iam-user"></a>

As an IAM administrator, you can add users to a group at any time\. This grants the users the permissions granted to the group\.

**To create an IAM user and add the user to a group**

1. In the navigation pane, choose **Users** and then choose **Add user**\.

1. For **User name**, enter the names for one or more users\.

1. Select the check box next to **AWS Management Console access**\. Configure an auto\-generated or custom password\. You can optionally select **User must create a new password at next sign\-in** to require a password reset when the user first signs in\.

1. Choose **Next: Permissions**\.

1. Choose **Add user to group** and then select the group that you created\.

1. Choose **Next: Tags**\. You can optionally add tags to your users\.

1. Choose **Next: Review**\. When you are ready, choose **Create user**\.

## Example IAM policies<a name="example-iam-policies"></a>

You can create permissions policies that grant permissions to IAM users\. You can grant users access to AWS Artifact reports and the ability to accept and download agreements on behalf of either a single account or an organization\.

The following example policies show permissions that you can assign to IAM users based on the level of access that they need\.
+ [Example policies to manage reports](#example-policy-manage-reports)
+ [Example policies to manage agreements](#example-policy-manage-agreements)
+ [Example policies to integrate with AWS Organizations](#example-policy-integrate-with-organizations)
+ [Example policies to manage agreements for the master account](#example-policy-agreements-master)
+ [Example policies to manage organizational agreements](#example-policy-organizational-agreements)<a name="example-policy-manage-reports"></a>

**Example policies to manage reports**  
The following policy grants permission to download all reports\.  

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
```
The following policy grants permission to download only the SOC, PCI, and ISO reports\.  

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
```<a name="example-policy-manage-agreements"></a>

**Example policies to manage agreements**  
The following policy grants permission to download all agreements\. IAM users must also have this permission to accept agreements\.  

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
```
The following policy grants permission to accept an agreement\.  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "artifact:AcceptAgreement",
                "artifact:DownloadAgreement"
            ],
            "Resource": [
                "*"
            ]
        }
    ]
}
```
The following policy grants permission to terminate an agreement\.  

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
```
The following policy grants permissions to manage single account agreements\.  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "artifact:AcceptAgreement",
                "artifact:DownloadAgreement",
                "artifact:TerminateAgreement"
            ],
            "Resource": [
                "arn:aws:artifact::*:customer-agreement/*",
                "arn:aws:artifact:::agreement/*"
            ]
        }
    ]
}
```<a name="example-policy-integrate-with-organizations"></a>

**Example policies to integrate with AWS Organizations**  
The following policy grants permission to create the IAM role that AWS Artifact uses to integrate with AWS Organizations\. Your organization's master account must have these permissions to get started with organizational agreements\.  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "iam:ListRoles",
            "Resource": "arn:aws:iam::*:role/*"
        },
        {
            "Effect": "Allow",
            "Action": "iam:CreateRole",
            "Resource": "arn:aws:iam::*:role/service-role/AWSArtifactAccountSync"
        },
        {
            "Effect": "Allow",
            "Action": "iam:AttachRolePolicy",
            "Resource": "arn:aws:iam::*:role/service-role/AWSArtifactAccountSync",
            "Condition": {
                "ArnEquals": {
                    "iam:PolicyARN": "arn:aws:iam::aws:policy/service-role/AWSArtifactAccountSync"
                }
            }
        }
    ]
}
```
The following policy grants permission to grant AWS Artifact the permissions to use AWS Organizations\. Your organization's master account must have these permissions to get started with organizational agreements\.  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "organizations:EnableAWSServiceAccess",
                "organizations:DescribeOrganization",
                "organizations:ListAWSServiceAccessForOrganization"
            ],
            "Resource": "*"
        }
    ]
}
```<a name="example-policy-agreements-master"></a>

**Example policies to manage agreements for the master account**  
The following policy grants permissions to manage agreements for the master account\.  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "artifact:AcceptAgreement",
                "artifact:DownloadAgreement",
                "artifact:TerminateAgreement"
            ],
            "Resource": [
                "arn:aws:artifact::*:customer-agreement/*",
                "arn:aws:artifact:::agreement/*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": "iam:ListRoles",
            "Resource": "arn:aws:iam::*:role/*"
        },
        {
            "Effect": "Allow",
            "Action": "iam:CreateRole",
            "Resource": "arn:aws:iam::*:role/service-role/AWSArtifactAccountSync"
        },
        {
            "Effect": "Allow",
            "Action": "iam:AttachRolePolicy",
            "Resource": "arn:aws:iam::*:role/service-role/AWSArtifactAccountSync",
            "Condition": {
                "ArnEquals": {
                    "iam:PolicyARN": "arn:aws:iam::aws:policy/service-role/AWSArtifactAccountSync"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "organizations:DescribeOrganization",
                "organizations:EnableAWSServiceAccess",
                "organizations:ListAccounts",
                "organizations:ListAWSServiceAccessForOrganization"
                
            ],
            "Resource": "*"
        }
    ]
}
```<a name="example-policy-organizational-agreements"></a>

**Example policies to manage organizational agreements**  
The following policy grants permissions to manage organizational agreements\. Another user with the required permissions must set up the organizational agreements\.  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "artifact:AcceptAgreement",
                "artifact:DownloadAgreement",
                "artifact:TerminateAgreement"
            ],
            "Resource": [
                "arn:aws:artifact::*:customer-agreement/*",
                "arn:aws:artifact:::agreement/*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "organizations:DescribeOrganization"
            ],
            "Resource": "*"
        }
    ]
}
```
The following policy grants permissions to view organizational agreements\.  

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
                "arn:aws:artifact::*:customer-agreement/*",
                "arn:aws:artifact:::agreement/*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "organizations:DescribeOrganization"
            ],
            "Resource": "*"
        }
    ]
}
```