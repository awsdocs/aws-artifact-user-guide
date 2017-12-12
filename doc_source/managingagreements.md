# Managing Your Agreements<a name="managingagreements"></a>

AWS Artifact Agreements is a feature of the AWS Artifact service that enables you to review, accept, and track the status of a Business Associate Addendum \(BAA\) agreement\. A BAA typically is required for companies that are subject to the Health Insurance Portability and Accountability Act \(HIPAA\) to ensure that protected health information \(PHI\) is appropriately safeguarded\. You can use AWS Artifact Agreements to enter into a BAA agreement with AWS and designate an AWS account that can legally process protected health information \(PHI\)\. You also can manage the designation of your HIPAA accounts and view your account’s HIPAA status at any time\. 

## Entering into an Agreement with AWS<a name="enteragreement"></a>

By default, only users with administrative privileges can enter into an agreement or manage the HIPAA status of an AWS account\. If you are an administrator, you can give IAM users and federated users with roles permissions to access and manage one or more of your agreements\. 

**Important**  
Before you enter into an agreement, we recommend that you consult with your legal, privacy, and compliance team\.

**To enter into an agreement with AWS**

1. Sign in to the AWS Management Console and open the AWS Artifact console at [https://console\.aws\.amazon\.com/artifact/](https://console.aws.amazon.com/artifact/)\.

1. On the AWS Artifact dashboard, choose **Agreements**\.

1. Under **AWS Artifact Nondisclosure Agreement**, choose **Download and review AWS Artifact NDA**\.

1. Review the document, and then select the check box to indicate that you agree with the content\.
**Note**  
The nondisclosure agreement is a legally binding contract\. We recommend that you read it closely\.

1. Choose **Accept the AWS Artifact NDA**\.

1. Under **AWS Business Associate Addendum**, choose **Download and review AWS BAA**\.

1. Review the document, select the check box, and then choose **Accept NDA and download AWS BAA**\. 

1. Select all three check boxes to indicate that you agree with the content\. 

1. Choose **Accept AWS BAA and designate HIPAA Account**\.

## Terminating an Agreement with AWS<a name="terminateagreement"></a>

 If you used the AWS Artifact console to enter into a Business Associate Addendum \(BAA\) agreement, you can use the console to terminate that agreement\. 

**Note**  
If you didn’t use the AWS Artifact console to enter into an agreement, you can’t use the console to terminate the agreement\. Instead, you must send an email to [aws\-hipaa@amazon\.com](mailto:aws-hipaa@amazon.com) to request the termination\.

**To terminate your online agreement with AWS**

1. Sign in to the AWS Management Console and open the AWS Artifact console at [https://console\.aws\.amazon\.com/artifact/](https://console.aws.amazon.com/artifact/)\.

1. On the AWS Artifact dashboard, choose **Agreements**\.

1. Under **AWS Business Associate Addendum**, choose **Terminate AWS BAA for this account**\. 

1. Select all four check boxes to indicate that you agree to terminate\. 

1. Choose **Terminate AWS BAA for this account**\. When prompted, choose it again\.

## Managing an Existing Offline Agreement<a name="manageofflineagreement"></a>

If you have an existing offline agreement, AWS Artifact Agreements will display **Offline Business Associate Addendum \(BAA\)**, which indicates it has been accepted\.