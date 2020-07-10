# How do I add a replication rule to an S3 bucket?<a name="enable-replication"></a>

Replication is the automatic, asynchronous copying of objects across buckets in the same or different AWS Regions\. Replication copies newly created objects and object updates from a source bucket to a destination bucket\. For more information about replication concepts and how to use replication with the AWS CLI, AWS SDKs, and the Amazon S3 REST APIs, see [Replication](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication.html) in the *Amazon Simple Storage Service Developer Guide*\. 

Replication requires versioning to be enabled on both the source and destination buckets\. To review the full list of requirements, see [Requirements for Replication](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication.html#replication-requirements) in the *Amazon Simple Storage Service Developer Guide*\. For more information about versioning, see [How do I enable or suspend versioning for an S3 bucket?](enable-versioning.md)

The object replicas in the destination bucket are exact replicas of the objects in the source bucket\. They have the same key names and the same metadata—for example, creation time, owner, user\-defined metadata, version ID, access control list \(ACL\), and storage class\. Optionally, you can explicitly specify a different storage class for object replicas\. And regardless of who owns the source bucket or the source object, you can choose to change replica ownership to the AWS account that owns the destination bucket\. For more information, see [Changing the replica owner](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-change-owner.html) in the *Amazon Simple Storage Service Developer Guide*\. 

You can use S3 Replication Time Control \(S3 RTC\) to replicate your data in the same AWS Region or across different AWS Regions in a predictable timeframe\. S3 RTC replicates 99\.99 percent of new objects stored in Amazon S3 within 15 minutes and most objects within seconds\. For more information, see [Replicating Objects Using S3 Replication Time Control \(S3 RTC\)](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-time-control.html) in the *Amazon Simple Storage Service Developer Guide*\.

**Note about replication and lifecycle rules**  
Metadata for an object remains identical between original objects and replica objects\. Lifecycle rules abide by the creation time of the original object, and not by when the replicated object becomes available in the destination bucket\. However, lifecycle does not act on objects that are pending replication until replication is complete\.

You use the Amazon S3 console to add replication rules to the source bucket\. Replication rules define which source bucket objects to replicate and the destination bucket where the replicated objects are stored\. You can create a rule to replicate all the objects in a bucket or a subset of objects with a specific key name prefix, one or more object tags, or both\. A destination bucket can be in the same AWS account as the source bucket, or it can be in a different account\.

If you specify an object version ID to delete, Amazon S3 deletes that object version in the source bucket\. But it doesn't replicate the deletion in the destination bucket\. In other words, it doesn't delete the same object version from the destination bucket\. This protects data from malicious deletions\.

If the destination bucket is in a different account from the source bucket, you must add a bucket policy to the destination bucket to grant the owner of the source bucket account permission to replicate objects in the destination bucket\. The Amazon S3 console builds this required bucket policy for you to copy and add to the destination bucket in the other account\. 

When you add a replication rule to a bucket, the rule is enabled by default, so it starts working as soon as you save it\. 

**Topics**
+ [Adding a replication rule when the destination bucket is in the same AWS account](#enable-replication-add-rule)
+ [Adding a replication rule when the destination bucket is in a different AWS account](#enable-replication-cross-account-destination)
+ [More info](#enable-replication-moreinfo)

## Adding a replication rule when the destination bucket is in the same AWS account<a name="enable-replication-add-rule"></a>

Follow these steps to configure a replication rule when the destination bucket is in the same AWS account as the source bucket\.

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want\.  
![\[Console screenshot showing bucket name list with bucket name selected.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Management**, choose **Replication**, and then choose **Add rule**\.  
![\[Console screenshot showing Management tab with Replication and Add rule selected.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-management-tab-replication.png)

1. In the **Replication rule** wizard, under **Set source**, you have the following options for setting the replication source:
   + To replicate the whole bucket, choose **Entire bucket *bucket\-name***\. 
   + To replicate all objects that have the same prefix \(for example, all objects that have names that begin with the string `pictures`\), choose **Prefix or tags**\. Enter a prefix in the box, choose the prefix from the drop\-down list, and then press **Enter**\. If you enter a prefix that is the name of a folder, you must use **/** \(forward slash\) as the last character \(for example, `pictures/`\)\. For more information about prefixes, see [Object Keys](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html#object-keys) in the *Amazon Simple Storage Service Developer Guide*\.
   + To replicate all objects with one or more object tags, enter a tag in the box, choose the tag from the drop\-down list, and then press **Enter**\. Enter a tag value and then press **Enter**\. Repeat the procedure to add another tag\. You can combine a prefix and tags\. For more information about object tags, see [Object Tagging](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html) in the *Amazon Simple Storage Service Developer Guide*\.  
![\[Console screenshot showing replication rule wizard step one, set source.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-source.png)

   The new schema supports prefix and tag filtering and the prioritization of rules\. For more information about the new schema, see [ Replication Configuration Backward Compatibility](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-add-config.html#replication-backward-compat-considerations) in the *Amazon Simple Storage Service Developer Guide*\. The developer guide describes the XML used with the Amazon S3 API that works behind the user interface\. In the developer guide, the new schema is described as *replication configuration XML V2*\.

1. To replicate objects in the source bucket that are encrypted with AWS Key Management Service \(AWS KMS\), under **Replication criteria**, select **Replicate objects encrypted with AWS KMS**\. Under **Choose one or more keys for decrypting source objects** are the source AWS KMS customer master keys \(CMKs\) that you allow replication to use\. All source CMKs are included by default\. You can choose to narrow the CMK selection\. 

   Objects encrypted by AWS KMS CMKs that you do not select are not replicated\. A CMK or a group of CMKs is chosen for you, but you can choose the CMKs if you want\. For information about using AWS KMS with replication, see [Replicating Objects Created with Server\-Side Encryption \(SSE\) Using Encryption Keys Stored in AWS KMS](https://docs.aws.amazon.com/AmazonS3/latest/dev/crr-replication-config-for-kms-objects.html) in the *Amazon Simple Storage Service Developer Guide*\.  
![\[Console screenshot showing replication rule wizard step one, select AWS KMS.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-source-kms.png)
**Important**  
When you replicate objects that are encrypted with AWS KMS, the AWS KMS request rate doubles in the source Region and increases in the destination Region by the same amount\. These increased call rates to AWS KMS are due to the way that data is re\-encrypted using the customer master key \(CMK\) that you define for the replication destination Region\. AWS KMS has a request rate limit that is per calling account per Region\. For information about the limit defaults, see [AWS KMS Limits \- Requests per Second: Varies](https://docs.aws.amazon.com/kms/latest/developerguide/limits.html#requests-per-second) in the *AWS Key Management Service Developer Guide*\.   
If your current Amazon S3 PUT object request rate during replication is more than half the default AWS KMS rate limit for your account, we recommend that you request an increase to your AWS KMS request rate limit\. To request an increase, create a case in the AWS Support Center at [Contact Us](https://aws.amazon.com/contact-us/)\. For example, suppose that your current PUT object request rate is 1,000 requests per second and you use AWS KMS to encrypt your objects\. In this case, we recommend that you ask AWS Support to increase your AWS KMS rate limit to 2,500 requests per second, in both your source and destination Regions \(if different\), to ensure that there is no throttling by AWS KMS\.   
To see your PUT object request rate in the source bucket, view `PutRequests` in the Amazon CloudWatch request metrics for Amazon S3\. For information about viewing CloudWatch metrics, see [How do I configure request metrics for an S3 Bucket?](configure-metrics.md)

   Choose **Next**\.

1. To choose a destination bucket from the account that you're currently using, on the **Set destination** page, under **Destination bucket**, choose **Buckets in this account**\. Enter the name of the destination bucket for the replication, or choose a name in the drop\-down list\.

   If you want to choose a destination bucket from a different AWS account, see [Adding a replication rule when the destination bucket is in a different AWS account](#enable-replication-cross-account-destination)\.   
![\[Console screenshot showing destination bucket section with Buckets in this account selected.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination.png)

   If versioning is not enabled on the destination bucket, you get a warning message that contains an **Enable versioning** button\. Choose this button to enable versioning on the bucket\.

1. If you chose to replicate objects encrypted with AWS KMS, under **Destination encryption settings**, enter the Amazon Resource Name \(ARN\) of the AWS KMS CMK to use to encrypt the replicas in the destination bucket\. You can find the ARN for your AWS KMS CMK in the IAM console, under **Encryption keys**\.  Or, you can choose a CMK name from the drop\-down list\.

   For more information about creating an AWS KMS CMK, see [Creating Keys](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html) in the *AWS Key Management Service Developer Guide*\.
**Important**  
The Amazon S3 console lists only 100 AWS KMS CMKs per AWS Region\. If you have more than 100 CMKs in the same Region, you can see only the first 100 CMKs in the S3 console\. To use a KMS CMK that is not listed in the console, choose **Custom KMS ARN**, and enter the KMS CMK ARN\.  
![\[Console screenshot showing destination encryption settings.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-kms-key.png)

1. If you want to replicate your data into a specific storage class in the destination bucket, on the **Set destination** page, under **Destination Options**, select **Change the storage class for the replicated object\(s\)**\. Then choose the storage class that you want to use for the replicated objects in the destination bucket\. If you don't select this option, the storage class for replicated objects is the same class as the original objects\. 

   Similarly, if you want to change **Object Ownership** in the destination bucket, choose **Change object ownership to the destination bucket owner**\. For more information about this option, see [Adding a replication rule when the destination bucket is in a different AWS account](#enable-replication-cross-account-destination)\. 

   If you want to enable S3 Replication Time Control \(S3 RTC\) in your replication configuration, select **Replication time control**\.
**Note**  
When you use S3 RTC, additional per\-GB data transfer fees and CloudWatch metrics fees apply\.  
![\[Console screenshot showing replication time control settings.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/enable-replication-time-control.png)

   Choose **Next**\.

1. Set up an AWS Identity and Access Management \(IAM\) role that Amazon S3 can assume to replicate objects on your behalf\.

   To set up an IAM role, on the **Configure options** page, under **Select role**, do one of the following:
   + We highly recommend that you choose **Create new role** to have Amazon S3 create a new IAM role for you\. When you save the rule, a new policy is generated for the IAM role that matches the source and destination buckets that you choose\. The name of the generated role is based on the bucket names and uses the following naming convention: **replication\_role\_for\_*source\-bucket*\_to\_*destination\-bucket***\.
   + You can choose to use an existing IAM role\. If you do, you must choose a role that grants Amazon S3 the necessary permissions for replication\. Replication fails if this role does not grant Amazon S3 sufficient permissions to follow your replication rule\. 
**Important**  
When you add a replication rule to a bucket, you must have the `iam:PassRole` permission to be able to pass the IAM role that grants Amazon S3 replication permissions\. For more information, see [Granting a User Permissions to Pass a Role to an AWS Service](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_passrole.html) in the *IAM User Guide*\.  
![\[Console screenshot showing the IAM role settings for your replication.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-set-iam-role.png)

   Under **Rule name**, enter a name for your rule to help identify the rule later\. The name is required and must be unique within the bucket\.

1.  If the bucket has existing replication rules, you are instructed to set a priority for the rule\. You must set a priority for the rule to avoid conflicts caused by objects that are included in the scope of more than one rule\. In the case of overlapping rules, Amazon S3 uses the rule priority to determine which rule to apply\. The higher the number, the higher the priority\. For more information about rule priority, see [Replication configuration overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-add-config.html) in the *Amazon Simple Storage Service Developer Guide*\.

   Under **Status**, **Enabled** is selected by default\. An enabled rule starts to work as soon as you save it\. If you want to enable the rule later, select **Disabled**\.

   Choose **Next**\.  
![\[Console screenshot showing priority and status settings for replication rule.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-set-options.png)

1. On the **Review** page, review your replication rule\. If it looks correct, choose **Save**\. Otherwise, choose **Previous** to edit the rule before saving it\. 

1. After you save your rule, you can edit, enable, disable, or delete your rule on the **Replication** page\.   
![\[Console screenshot showing replication page with rule details and options.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-rules-page-one.png)

## Adding a replication rule when the destination bucket is in a different AWS account<a name="enable-replication-cross-account-destination"></a>

Follow these steps to configure a replication rule when the destination bucket is in a different AWS account than the source bucket\.

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want\.  
![\[Console screenshot showing bucket list with bucket name selected.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Management**, choose **Replication**, and then choose **Add rule**\.  
![\[Console screenshot showing management tab with Replication and Add rule buttons selected.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-management-tab-replication.png)

1. If you have never created a replication rule before, start with [Adding a replication rule when the destination bucket is in the same AWS account](#enable-replication-add-rule)\.

   On the **Replication rule** wizard **Set destination** page, under **Destination bucket**, choose **Buckets in another account**\. Then enter the name of the destination bucket and the account ID from a different AWS account\. Choose **Save**\.   
![\[Console screenshot showing choosing a destination bucket in a different AWS account.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-bucket-cross-account.png)

   After you save the destination bucket name and account ID, you might get a warning message telling you to add a bucket policy to the destination bucket so that Amazon S3 can verify whether versioning is enabled on the bucket\. You are presented with a bucket policy in a few steps that you can copy and add to the destination bucket in the other account\. For information about adding a bucket policy to an S3 bucket and versioning, see [How do I add an S3 Bucket policy?](add-bucket-policy.md) and [How do I enable or suspend versioning for an S3 bucket?](enable-versioning.md)  
![\[Warning message stating that S3 can't detect whether versioning is enabled on the destination bucket.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-x-account-error.png)

1. If you chose to replicate objects encrypted with AWS KMS, under **Destination encryption settings**, enter the Amazon Resource Name \(ARN\) AWS KMS CMK to use to encrypt the replicas in the destination bucket\. 

   For more information about creating an AWS KMS CMK, see [Creating Keys](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html) in the *AWS Key Management Service Developer Guide*\.  
![\[Console screenshot showing where to enter AWS KMS key to encrypt the objects in the destination bucket.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-kms-key-only.png)

1. On the **Set destination** page, under **Destination Options**:
   + To replicate your data into a specific storage class in the destination bucket, select **Change the storage class for the replicated object\(s\)**\. Then choose the storage class that you want to use for the replicated objects in the destination bucket\. If you don't select this option, the storage class for replicated objects is the same class as the original objects\.
   + To change the object ownership of the replica objects to the destination bucket owner, select **Change object ownership to destination owner**\. This option enables you to separate object ownership of the replicated data from the source\. If asked, type the account ID of the destination bucket\.

     When you select this option, regardless of who owns the source bucket or the source object, the AWS account that owns the destination bucket is granted full permission to replica objects\. For more information, see [Changing the Replica Owner](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-change-owner.html) in the *Amazon Simple Storage Service Developer Guide*\.
   + If you want to add S3 Replication Time Control \(S3 RTC\) to your replication configuration, select **Replication time control**\.
**Note**  
When you use S3 RTC, additional per\-GB data transfer fees and CloudWatch metrics fees apply\.  
![\[Console screenshot showing the Destination options for your replication.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/enable-replication-time-control.png)

   Choose **Next**\.

1. Set up an AWS Identity and Access Management \(IAM\) role that Amazon S3 can assume to perform replication of objects on your behalf\.

   To set up an IAM role, on the **Configure options** page, under **Select role**, do one of the following:
   + We highly recommend that you choose **Create new role** to have Amazon S3 create a new IAM role for you\. When you save the rule, a new policy is generated for the IAM role that matches the source and destination buckets that you choose\. The name of the generated role is based on the bucket names and uses the following naming convention: **replication\_role\_for\_*source\-bucket*\_to\_*destination\-bucket***\.
   + You can choose to use an existing IAM role\. If you do, you must choose a role that allows Amazon S3 to replicate objects from the source bucket to the destination bucket on your behalf\.  
![\[Console screenshot showing where you select an IAM role for your replication.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-permissions.png)

1. A bucket policy is provided on the **Configure options** page that you can copy and add to the destination bucket in the other account\. For information about adding a bucket policy to an S3 bucket, see [How do I add an S3 Bucket policy?](add-bucket-policy.md)  
![\[Console screenshot showing an example bucket policy for the destination bucket.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-permissions-policy.png)

1. If you chose to replicate objects encrypted with AWS KMS, an AWS KMS key policy is provided on the **Configure options** page\. You can copy this policy to add to the key policy for the AWS KMS CMK that you are using\. The key policy grants the source bucket owner permission to use the CMK\. For information about updating the key policy, see [Grant the source bucket owner permission to encrypt using the AWS KMS CMK](#enable-replication-kms-key-policy)\.   
![\[Console screenshot showing a destination bucket AWS KMS key policy.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-wizard-destination-kms-key-policy.png)

1. On the **Review** page, review your replication rule\. If it looks correct, choose **Save**\. Otherwise, choose **Previous** to edit the rule before saving it\. 

1. After you save your rule, you can edit, enable, disable, or delete your rule on the **Replication** page\.   
![\[Replication page displaying rule details and options.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-rules-page-cross-account.png)

1. Follow the instructions given on the **Replication** page under the warning message, The replication rule is saved, but additional settings are required in the destination account\. Sign out of the AWS account that you are currently in, and then sign in to the destination account\. 
**Important**  
Replication fails until you sign in to the destination account and complete the following steps\.

1. After you sign in to the destination account, choose the **Management** tab, choose **Replication**, and then choose **Receive objects** on the **Actions** menu\. 

1. On the **Receive objects** page, you can do the following:
   + Enable versioning on the destination bucket\.
   + Apply the bucket policy provided by Amazon S3 to the destination bucket\.
   + Copy the AWS KMS key policy that you need to update the AWS KMS CMK that is being used to encrypt the replica objects in the destination bucket\. For information about updating the key policy, see [Grant the source bucket owner permission to encrypt using the AWS KMS CMK](#enable-replication-kms-key-policy)\.  
![\[Console screenshot showing receive objects page.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/crr-receive-objects.png)

### Grant the source bucket owner permission to encrypt using the AWS KMS CMK<a name="enable-replication-kms-key-policy"></a>

You must grant permissions to the account of the source bucket owner to encrypt using your AWS KMS CMK with a key policy\. The following procedure describes how to use the AWS Identity and Access Management \(IAM\) console to modify the key policy for the AWS KMS CMK that is being used to encrypt the replica objects in the destination bucket\.

**To grant permissions to encrypt using your AWS KMS CMK**

1. Sign in to the AWS Management Console using the AWS account that owns the AWS KMS CMK\. Open the AWS KMS console at [https://console\.aws\.amazon\.com/kms](https://console.aws.amazon.com/kms)\.

1. Choose the alias of the CMK that you want to encrypt with\.

1. In the **Key Policy** section of the page, choose **Switch to policy view**\.

1. Choose **Edit** to edit **Key Policy**\.

1. Using the **Key Policy** editor, insert the key policy provided by Amazon S3 into the existing key policy, and then choose **Save Changes**\. You might want to add the policy to the end of the existing policy\. 

For more information about creating and editing AWS KMS CMKs, see [Getting Started](https://docs.aws.amazon.com/kms/latest/developerguide/getting-started.html) in the *AWS Key Management Service Developer Guide*\. 

## More info<a name="enable-replication-moreinfo"></a>
+ [How do I manage the replication rules for an S3 Bucket?](disable-replication.md)
+ [How do I enable or suspend versioning for an S3 bucket?](enable-versioning.md)
+ [Replication](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication.html) in the *Amazon Simple Storage Service Developer Guide*