# Managing an agreement for multiple accounts in AWS Artifact<a name="manage-org-agreement"></a>

If you are the owner of the master account of an AWS Organizations organization, you can accept an agreement on behalf of all accounts in your organization\. You must be signed in to the master account with the correct AWS Artifact permissions to accept or terminate organization agreements\. Users of member accounts with `describeOrganizations` permissions can view the organization agreements that are accepted on their behalf\. 

If your account is not part of an organization, you can create or join an organization by following the instructions in [Creating and managing an organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org.html) in the *AWS Organizations User Guide*\.

AWS Organizations has two available feature sets: *consolidated billing features* and *all features*\. To use AWS Artifact for your organization, the organization that you belong to must be enabled for [all features](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_getting-started_concepts.html#feature-set)\. If your organization is configured only for consolidated billing, see [Enabling all features in your organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_support-all-features.html) in the *AWS Organizations User Guide*\.

If a member account is removed from an organization, that member account will no longer be covered by organization agreements\. Master account administrators should communicate this to member accounts before removing member accounts from the organization, so that member accounts can put new agreements in place if necessary\. A list of active organization agreements can be viewed in [AWS Artifact Organization agreements](https://console.aws.amazon.com/artifact/home?#!/agreements?tab=organizationAgreements)\.

For more information, see [Managing the AWS accounts in your organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_accounts.html) in the *AWS Organizations User Guide*\.

## Accepting an agreement for your organization<a name="org-agreement"></a>

You can accept an agreement on behalf of all member accounts in your organization in AWS Organizations\. Before you accept an agreement, we recommend that you consult with your legal, privacy, and compliance team\.

**Required permissions**  
To accept an agreement, the owner of the master account must have the following permissions:

```
artifact:DownloadAgreement
artifact:AcceptAgreement
organizations:DescribeOrganization 
organizations:EnableAWSServiceAccess 
organizations:ListAWSServiceAccessForOrganization
iam:ListRoles 
iam:CreateRole 
iam:AttachRolePolicy
```

For more information, see [Identity and access management](security-iam.md)\.<a name="enter-org-agreement"></a>

**To accept an agreement for an organization**

1. Open the AWS Artifact console at [https://console\.aws\.amazon\.com/artifact/](https://console.aws.amazon.com/artifact/)\. 

1. On the AWS Artifact dashboard, choose **Agreements**\.

1. Choose the **Organization agreements** tab\.

1. Expand the section of the agreement\.

1. Choose **Download and review**\.

1. Read the **Terms and Conditions**\. When you are finished, choose **Accept and download**\.

1. Review the agreement and then select the check boxes to indicate that you agree\.

1. Choose **Accept** to accept the agreement for all existing and future accounts in your organization\.\.

## Terminating an organization agreement<a name="terminate-org-agreement"></a>

If you used the AWS Artifact console to accept an agreement on behalf of all member accounts in an organization, you can use the console to terminate that agreement\. Otherwise, see [Offline agreements](manage-offline-agreement.md)\.

**Required permissions**  
To terminate an agreement, the owner of the master account must have the following permissions:

```
artifact:DownloadAgreement
artifact:TerminateAgreement
organizations:DescribeOrganization 
organizations:EnableAWSServiceAccess 
organizations:ListAWSServiceAccessForOrganization
iam:ListRoles 
iam:CreateRole 
iam:AttachRolePolicy
```

For more information, see [Identity and access management](security-iam.md)\.

**To terminate your online organization agreement with AWS**

1. Open the AWS Artifact console at [https://console\.aws\.amazon\.com/artifact/](https://console.aws.amazon.com/artifact/)\. 

1. On the AWS Artifact dashboard, choose **Agreements**\.

1. Choose the **Organization agreements** tab\.

1. Select the agreement and choose **Terminate agreement**\.

1. Select all check boxes to indicate that you agree to terminate the agreement\.

1. Choose **Terminate**\. When prompted for confirmation, choose **Terminate**\.