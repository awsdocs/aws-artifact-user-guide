# Managing an agreement for a single account in AWS Artifact<a name="manage-single-agreement"></a>

You can accept agreements for just your account, even if your account is a member account in an organization in AWS Organizations\. For more information about AWS Organizations, see the [AWS Organizations User Guide](https://docs.aws.amazon.com/organizations/latest/userguide/)\.

## Accepting an agreement with AWS<a name="accept-agreement"></a>

Before you accept an agreement, we recommend that you consult with your legal, privacy, and compliance team\.

**Required permissions**  
If you're an administrator of an account, you can grant IAM users and federated users with roles the permissions to access and manage one or more of your agreements\. By default, only users with administrative privileges can accept an agreement\. To accept an agreement, IAM and federated users must have the following permissions:

```
artifact:DownloadAgreement
artifact:AcceptAgreement
```

For more information, see [Identity and access management](security-iam.md)\.

**To accept an agreement with AWS**

1. Open the AWS Artifact console at [https://console\.aws\.amazon\.com/artifact/](https://console.aws.amazon.com/artifact/)\. 

1. On the AWS Artifact navigation pane, choose **Agreements**\.

1. Choose the **Account agreements** tab\.

1. Expand the section of the agreement\.

1. Choose **Download and review**\.

1. Read the **Terms and Conditions**\. When you are finished, choose **Accept and download**\.

1. Review the agreement and then select the check boxes to indicate that you agree\.

1. Choose **Accept** to accept the agreement for your account\.

## Terminating an agreement with AWS<a name="terminate-agreement"></a>

If you used the AWS Artifact console to accept an agreement, you can use the console to terminate that agreement\. Otherwise, see [Offline agreements](manage-offline-agreement.md)\.

**Required permissions**  
To terminate an agreement, IAM and federated users must have the following permissions:

```
artifact:TerminateAgreement
```

For more information, see [Identity and access management](security-iam.md)\.

**To terminate your online agreement with AWS**

1. Open the AWS Artifact console at [https://console\.aws\.amazon\.com/artifact/](https://console.aws.amazon.com/artifact/)\. 

1. On the AWS Artifact navigation pane, choose **Agreements**\.

1. Choose the **Account agreements** tab\.

1. Select the agreement and choose **Terminate agreement**\.

1. Select all check boxes to indicate that you agree to terminate the agreement\.

1. Choose **Terminate**\. When prompted for confirmation, choose **Terminate**\.