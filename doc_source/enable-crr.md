# How Do I Add a Cross\-Region Replication \(CRR\) Rule to an S3 Bucket?<a name="enable-crr"></a>

Cross\-region replication is the automatic, asynchronous copying of objects across buckets in different AWS Regions\. Cross\-region replication replicates newly created objects, object updates, and object deletions from a source bucket to a destination bucket in a different AWS Region\.  

Cross\-region replication requires that the source and destination buckets be in different AWS Regions, and versioning must be enabled on both the source and destination buckets\. To review the full list of requirements, see [Requirements for Cross\-Region Replication](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html#crr-requirements) in the *Amazon Simple Storage Service Developer Guide*\. For more information about versioning, see [How Do I Enable or Suspend Versioning for an S3 Bucket?](enable-versioning.md)\.

The object replicas in the destination bucket are exact replicas of the objects in the source bucket\. They have the same key names and the same metadata—for example, creation time, owner, user\-defined metadata, version ID, access control list \(ACL\), and storage class\. Optionally, you can explicitly specify a different storage class for object replicas\. And regardless of who owns the source bucket or the source object, you can choose to change replica ownership to the AWS account that owns the destination bucket\. For more information, see [CRR: Change Replica Owner](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr-change-owner.html) in the *Amazon Simple Storage Service Developer Guide*\. 

The time it takes for Amazon S3 to replicate an object depends on the object size\. It can take up to several hours to replicate a large\-sized object\.

**Note about replication and lifecycle rules**  
Metadata for an object remains identical between original objects and replica objects\. Lifecycle rules abide by the creation time of the original object, and not by when the replicated object becomes available in the destination bucket\. However, lifecycle does not act on objects that are pending replication until replication is complete\.

You use the Amazon S3 console to add replication rules to the source bucket\. Replication rules define which source bucket objects to replicate and the destination bucket where the replicated objects are stored\. You can create rules to replicate all the objects in a bucket or a subset of objects with specific key name prefixes \(that is, objects that have names that begin with a common string\)\. A destination bucket can be in the same AWS account as the source bucket, or it can be in a different account\. The destination bucket must always be in a different Region than the source bucket\. 

If the destination bucket is in a different account from the source bucket, you must add a bucket policy to the destination bucket to grant the owner of the source bucket account permission to replicate objects in the destination bucket\. The Amazon S3 console builds this required bucket policy for you to copy and add to the destination bucket in the other account\. 

When you add a replication rule to a bucket, the rule is enabled by default, so it starts working as soon as you save it\. 



## Adding a Cross\-Region Replication Rule to an S3 Bucket<a name="enable-crr-add-rule"></a>

**To add a cross\-region replication rule to an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want\.  
![\[Bucket name list with bucket name selected\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Management**, choose **Replication**, and then choose **Add rule**\.  
![\[Management tab with Replication and Add rule selected\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-management-tab-replication.png)

1. To replicate the whole bucket, in the **Replication rule** dialog box, under **Source**, choose **All contents in *bucket\-name***\. To replicate all objects that have the same prefix \(for example, all objects that have names that begin with the string `pictures`\), choose **Prefix in this bucket**\. For example, all objects in a folder named pictures\. If you enter a prefix that is the name of a folder, you must use **/** \(forward slash\) as the last character \(for example, `pictures/`\)\. 

   Under **Status**, **Enabled** is selected by default\. An enabled rule starts to work as soon as you save it\. If you want to enable the rule later, select **Disabled**\.  
![\[Replication rule wizard step one, configure the source.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-source.png)

1.  To replicate objects in the source bucket that are encrypted with AWS KMS, under **Replication criteria**, select **Replicate objects encrypted with AWS KMS**\. Under **Choose one or more keys for decrypting source objects** are the source AWS KMS key or keys that you allow cross\-region replication to use\. All source keys are included by default\. You can choose to narrow the key selection\. 

   Objects encrypted by AWS KMS keys that you do not select are not replicated by cross\-region replication\. A key or a group of keys is chosen for you, but you can choose the keys if you want\. For information about using AWS KMS with cross\-region replication, see [CRR: Replicating Objects Created with Server\-Side Encryption \(SSE\) Using AWS KMS\-Managed Encryption Key](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.crr-replication-config-for-kms-objects.html) in the *Amazon Simple Storage Service Developer Guide*\.   
![\[Replication rule wizard step one, select AWS KMS.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-source-kms.png)
**Important**  
AWS KMS has a request rate limit\. For more information, see [AWS KMS limits](http://docs.aws.amazon.com/kms/latest/developerguide/limits.html#requests-per-second)\. AWS KMS support for cross\-region replication increases the KMS request rate for your account\. As a best practice, we recommend requesting an increase in your AWS KMS API rate limit by creating a case in the AWS Support Center\. For information about contacting AWS Support, see [Contact Us](https://aws.amazon.com/contact-us/)\. We recommend confirming the rate limit increase before enabling cross\-region replication with AWS KMS\.

   Choose **Next**\.

1. To choose a destination bucket from the account that you're currently using, on the **Destination** page, under **Destination bucket**, choose **Buckets in this account**\. Type the name of the destination bucket for the replication, or choose a name in the drop\-down list\. If you don't see the bucket that you want in the list, confirm that the bucket exists and that it's in a different Region than the source bucket\.

   If you want to choose a destination bucket from a different AWS account, see [Configuring a CRR Rule When the Destination Bucket is in a Different AWS Account](#enable-crr-cross-account-destination)\.   
![\[Destination bucket section with Buckets in this account selected\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination.png)

   If versioning is not enabled on the destination bucket, you get a warning message that contains an **Enable versioning** button\. Choose this button to enable versioning on the bucket\.  
![\[Error message stating that the destination bucket doesn't have versioning
              enabled\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-enable-versioning.png)

1. If you chose to replicate objects encrypted with AWS KMS, under **Destination encryption settings**, type the Amazon Resource Name \(ARN\) of the AWS KMS key to use to encrypt the replicas in the destination bucket\. You can find the ARN for your AWS KMS key in the IAM console, under **Encryption keys**\.  Or, you can choose a key name from the drop\-down list\.

   For more information about creating an AWS KMS key, see [Creating Keys](http://docs.aws.amazon.com/kms/latest/developerguide/UsingServerSideEncryption.html) in the *AWS Key Management Service Developer Guide*\.  
![\[Enter a AWS KMS key to encrypt the objects in the destination bucket.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-kms-key.png)

1. If you want to replicate your data into a specific storage class in the destination bucket, on the **Destination** page, under **Options**, select **Change the storage class for the replicated object\(s\)**\. Then choose the storage class that you want to use for the replicated objects in the destination bucket\. If you don't select this option, the storage class for replicated objects is the same class as the original objects\.  
![\[Destination options with Change the storage class for replicated objects
              selected\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-class.png)

   Choose **Next**\.

1. Set up an AWS Identity and Access Management \(IAM\) role that Amazon S3 can assume to perform cross\-region replication of objects on your behalf\.

   To set up an IAM role, on the **Permissions** page, under **Select role**, do one of the following:

   + We highly recommend that you choose **Create new role** to have Amazon S3 create a new IAM role for you\. When you save the rule, a new policy is generated for the IAM role that matches the source and destination buckets that you choose\. The name of the generated role is based on the bucket names and uses the following naming convention: **replication\_role\_for\_*source\-bucket*\_to\_*destination\-bucket***\.

   + You can choose to use an existing IAM role\. If you do, you must choose a role that grants Amazon S3 the necessary permissions for replication\. Replication fails if this role does not grant Amazon S3 sufficient permissions to follow your replication rule\.   
![\[Select an IAM role for your replication\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-permissions.png)

   Choose **Next**\.

1. On the **Review** page, review your replication rule\. If it looks correct, choose **Save**\. Otherwise, choose **Previous** to edit the rule before saving it\.   
![\[Replication rule wizard review page.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-review-one.png)

1. After you save your rule, you can edit, enable, disable, or delete your rule on the **Replication** page\.   
![\[Replication page displaying rule details and options\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-rules-page-one.png)

## Configuring a CRR Rule When the Destination Bucket is in a Different AWS Account<a name="enable-crr-cross-account-destination"></a>

This section describes how to configure cross\-region replication rule when the destination bucket is in a different AWS account than the source bucket\.

**To add a cross\-region replication rule when the destination bucket is in a different AWS account than the source bucket**

1. If you have never created a cross\-region replication rule before, start with [Adding a Cross\-Region Replication Rule to an S3 Bucket](#enable-crr-add-rule)\.

   On the **Replication rule** wizard **Destination** page, under **Destination bucket**, choose **Buckets in another account**\. Then type the name of the destination bucket and the account ID from a different AWS account\. Choose **Save**\.   
![\[Choose a destination bucket in a different AWS account\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-bucket-cross-account.png)

   After you save the destination bucket name and account ID, you might get a warning message indicating that you must add a bucket policy to the destination bucket so that Amazon S3 can verify whether versioning is enabled on the bucket\. You can copy the bucket policy from the **Permissions** page, and then add the policy to the destination bucket in the other account\. For information about adding a bucket policy to an S3 bucket, see [How Do I Add an S3 Bucket Policy?](add-bucket-policy.md)\.  
![\[Warning message stating that S3 can't detect whether versioning is enabled on
              the destination bucket\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-x-account-error.png)

1. If you chose to replicate objects encrypted with AWS KMS, under **Destination encryption settings**, type the Amazon Resource Name \(ARN\) AWS KMS key to use to encrypt the replicas in the destination bucket\. 

   For more information about creating an AWS KMS key, see [Creating Keys](http://docs.aws.amazon.com/kms/latest/developerguide/UsingServerSideEncryption.html) in the *AWS Key Management Service Developer Guide*\.  
![\[Enter an AWS KMS key to encrypt the objects in the destination bucket.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-kms-key-only.png)

1. If you want to replicate your data into a specific storage class in the destination bucket, on the **Destination** page, under **Options**, select **Change the storage class for the replicated object\(s\)**\. Then choose the storage class that you want to use for the replicated objects in the destination bucket\. If you don't select this option, the storage class for replicated objects is the same class as the original objects\.

1. To change the object ownership of the replica objects to the destination bucket owner, under **Options**, select **Change object ownership to destination owner**\. This option enables you to separate object ownership of the replicated data from the source\. If asked, type the account ID of the destination bucket\.

   When you select this option, regardless of who owns the source bucket or the source object, the AWS account that owns the destination bucket is granted full permission to replica objects\. For more information, see [CRR: Change Replica Owner](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr-change-owner.html) in the *Amazon Simple Storage Service Developer Guide*\.  
![\[Enter an AWS KMS key to encrypt the objects in the destination bucket.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-change-object-owner.png)

1. Set up an AWS Identity and Access Management \(IAM\) role that Amazon S3 can assume to perform cross\-region replication of objects on your behalf\.

   To set up an IAM role, on the **Permissions** page, under **Select role**, do one of the following:

   + We highly recommend that you choose **Create new role** to have Amazon S3 create a new IAM role for you\. When you save the rule, a new policy is generated for the IAM role that matches the source and destination buckets that you choose\. The name of the generated role is based on the bucket names and uses the following naming convention: **replication\_role\_for\_*source\-bucket*\_to\_*destination\-bucket***\.

   + You can choose to use an existing IAM role\. If you do, you must choose a role that allows Amazon S3 to replicate objects from the source bucket to the destination bucket on your behalf\.  
![\[Select an IAM role for your replication\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-permissions.png)

1. A bucket policy is provided on the **Permissions** page that you can copy and add to the destination bucket in the other account\. For information about adding a bucket policy to an S3 bucket, see [How Do I Add an S3 Bucket Policy?](add-bucket-policy.md)\.  
![\[Example bucket policy for the destination bucket\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-permissions-policy.png)

1. If you chose to replicate objects encrypted with AWS KMS, an AWS KMS key policy is provided on the **Permissions** page\. You can copy this policy to add to the key policy for the AWS KMS key customer master key \(CMK\) that you are using\. The key policy grants the source bucket owner permission to use the key\. For information about updating the key policy, see [Grant the Source Bucket Owner Permission to Encrypt Using the AWS KMS Key](#enable-crr-kms-key-policy)\.   
![\[Destination bucket AWS KMS key policy\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-kms-key-policy.png)

1. On the **Review** page, review your replication rule\. If it looks correct, choose **Save**\. Otherwise, choose **Previous** to edit the rule before saving it\.   
![\[Replication rule wizard Review page enabled\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-review.png)

1. After you save your rule, you can edit, enable, disable, or delete your rule on the **Replication** page\.   
![\[Replication page displaying rule details and options\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-rules-page-cross-account.png)

1. Follow the instructions given on the Replication page under the warning message **The CRR rule is saved, but additional settings are required in the destination account\.** Sign out of the AWS account that you are currently in, and then sign in to the destination account\. 
**Important**  
Cross\-region replication fails until you sign in to the destination account and complete the following steps\.

1. After you sign in to the destination account, choose the **Management** tab, choose Replication, and then choose **Receive objects** from the **More **menu\.   
![\[Replication page displaying rule details and options\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-more-menu-receive-objects.png)

1. From the Receive objects page, you can perform the following:

   + Enable versioning on the destination bucket\.

   + Apply the bucket policy provided by Amazon S3 to the destination bucket\.

   + Copy the AWS KMS key policy that you need to update the AWS KMS CMK key that is being used to encrypt the replica objects in the destination bucket\. For information about updating the key policy, see [Grant the Source Bucket Owner Permission to Encrypt Using the AWS KMS Key](#enable-crr-kms-key-policy)\.  
![\[Receive objects page\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-receive-objects.png)

### Grant the Source Bucket Owner Permission to Encrypt Using the AWS KMS Key<a name="enable-crr-kms-key-policy"></a>

You must grant permissions to the account of the source bucket owner to encrypt using your AWS KMS key with a key policy\. The following procedure describes how to use the AWS Identity and Access Management \(IAM\) console to modify the key policy for the AWS KMS customer master key \(CMK\) that is being used to encrypt the replica objects in the destination bucket\.

**To grant permissions to encrypt using your AWS KMS key**

1. Sign in to the AWS Management Console using the AWS account that owns the AWS KMS CMK\. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the left navigation pane, choose **Encryption keys**\.

1. For **Region**, choose the appropriate AWS Region\. Do not use the region selector in the navigation bar \(upper\-right corner\)\.

1. Choose the alias of the CMK that you want to encrypt with\.

1. In the **Key Policy** section of the page, choose **Switch to policy view**\.

1. Using the **Key Policy** editor, insert the key policy provided by Amazon S3 into the existing key policy, and then choose **Save Changes**\. You might want to add the policy to the end of the existing policy\. 

For more information about creating and editing AWS KMS CMKs, see [Getting Started](http://docs.aws.amazon.com/kms/latest/developerguide/getting-started.html) in the *AWS Key Management Service Developer Guide*\. 

## More Info<a name="enable-crr-moreinfo"></a>

+ [How Do I Manage the Cross\-Region Replication Rules for an S3 Bucket?](disable-crr.md)

+ [How Do I Enable or Suspend Versioning for an S3 Bucket?](enable-versioning.md)

+ [Cross\-Region Replication](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html) in the *Amazon Simple Storage Service Developer Guide*