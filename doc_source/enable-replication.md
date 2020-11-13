# How do I add a replication rule to an S3 bucket?<a name="enable-replication"></a>

Replication is the automatic, asynchronous copying of objects across buckets in the same or different AWS Regions\. Replication copies newly created objects and object updates from a source bucket to a destination bucket\. For more information about replication concepts and how to use replication with the AWS CLI, AWS SDKs, and the Amazon S3 REST APIs, see [Replication](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication.html) in the *Amazon Simple Storage Service Developer Guide*\. 

By default, replication only supports copying new Amazon S3 objects after it is enabled\. You can use replication to copy existing objects and clone them to a different bucket, but in order to do so, you must contact [AWS Support Center](https://console.aws.amazon.com/support/home#/)\. When you contact support, give your AWS Support case the subject “Replication for Existing Objects” and include the following information: 
+ Source bucket
+ Destination bucket
+ Estimated storage volume to replicate \(in terabytes\)
+ Estimated storage object count to replicate

Replication requires versioning to be enabled on both the source and destination buckets\. To review the full list of requirements, see [Requirements for Replication](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication.html#replication-requirements) in the *Amazon Simple Storage Service Developer Guide*\. For more information about versioning, see [How do I enable or suspend versioning for an S3 bucket?](enable-versioning.md)

The object replicas in the destination bucket are exact replicas of the objects in the source bucket\. They have the same key names and the same metadata—for example, creation time, owner, user\-defined metadata, version ID, access control list \(ACL\), and storage class\. Optionally, you can explicitly specify a different storage class for object replicas\. And regardless of who owns the source bucket or the source object, you can choose to change replica ownership to the AWS account that owns the destination bucket\. For more information, see [Changing the replica owner](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-change-owner.html) in the *Amazon Simple Storage Service Developer Guide*\. 

You can use S3 Replication Time Control \(S3 RTC\) to replicate your data in the same AWS Region or across different AWS Regions in a predictable timeframe\. S3 RTC replicates 99\.99 percent of new objects stored in Amazon S3 within 15 minutes and most objects within seconds\. For more information, see [Replicating Objects Using S3 Replication Time Control \(S3 RTC\)](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-time-control.html) in the *Amazon Simple Storage Service Developer Guide*\.

**Note about replication and lifecycle rules**  
Metadata for an object remains identical between original objects and replica objects\. Lifecycle rules abide by the creation time of the original object, and not by when the replicated object becomes available in the destination bucket\. However, lifecycle does not act on objects that are pending replication until replication is complete\.

You use the Amazon S3 console to add replication rules to the source bucket\. Replication rules define which source bucket objects to replicate and the destination bucket where the replicated objects are stored\. You can create a rule to replicate all the objects in a bucket or a subset of objects with a specific key name prefix, one or more object tags, or both\. A destination bucket can be in the same AWS account as the source bucket, or it can be in a different account\.

If you specify an object version ID to delete, Amazon S3 deletes that object version in the source bucket\. But it doesn't replicate the deletion in the destination bucket\. In other words, it doesn't delete the same object version from the destination bucket\. This protects data from malicious deletions\.

If the destination bucket is in a different account from the source bucket, you must add a bucket policy to the destination bucket to grant the owner of the source bucket account permission to replicate objects in the destination bucket\. For more information, see [Granting permissions when source and destination buckets are owned by different AWS accounts](https://docs.aws.amazon.com/AmazonS3/latest/dev/setting-repl-config-perm-overview.html#setting-repl-config-crossacct) in the *Amazon Simple Storage Service Developer Guide*\.

When you add a replication rule to a bucket, the rule is enabled by default, so it starts working as soon as you save it\. 

**Topics**
+ [Adding a replication rule](#enable-replication-add-rule)
+ [Grant the source bucket owner permission to encrypt using the AWS KMS CMK](#enable-replication-kms-key-policy)
+ [More info](#enable-replication-moreinfo)

## Adding a replication rule<a name="enable-replication-add-rule"></a>

Follow these steps to configure a replication rule when the destination bucket is in the same AWS account as the source bucket\.

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that you want\.

1. Choose **Management**, scroll down to **Replication rules**\. and then choose **Create replication rule**\.

1. Under **Rule name**, enter a name for your rule to help identify the rule later\. The name is required and must be unique within the bucket\.

1. Set up an AWS Identity and Access Management \(IAM\) role that Amazon S3 can assume to replicate objects on your behalf\.

   To set up an IAM role, on the **Replication rule configuration** section, under **IAM role**, do one of the following:
   + We highly recommend that you choose **Create new role** to have Amazon S3 create a new IAM role for you\. When you save the rule, a new policy is generated for the IAM role that matches the source and destination buckets that you choose\. The name of the generated role is based on the bucket names and uses the following naming convention: **replication\_role\_for\_*source\-bucket*\_to\_*destination\-bucket***\.
   + You can choose to use an existing IAM role\. If you do, you must choose a role that grants Amazon S3 the necessary permissions for replication\. Replication fails if this role does not grant Amazon S3 sufficient permissions to follow your replication rule\.
**Important**  
When you add a replication rule to a bucket, you must have the `iam:PassRole` permission to be able to pass the IAM role that grants Amazon S3 replication permissions\. For more information, see [Granting a User Permissions to Pass a Role to an AWS Service](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_passrole.html) in the *IAM User Guide*\.

1. Under **Status**, see that **Enabled** is selected by default\. An enabled rule starts to work as soon as you save it\. If you want to enable the rule later, select **Disabled**\.

1.  If the bucket has existing replication rules, you are instructed to set a priority for the rule\. You must set a priority for the rule to avoid conflicts caused by objects that are included in the scope of more than one rule\. In the case of overlapping rules, Amazon S3 uses the rule priority to determine which rule to apply\. The higher the number, the higher the priority\. For more information about rule priority, see [Replication configuration overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-add-config.html) in the *Amazon Simple Storage Service Developer Guide*\.

1. In the **Replication rule configuration**, under **Source bucket**, you have the following options for setting the replication source:
   + To replicate the whole bucket, choose **This rule applies to all objects in the bucket**\. 
   + To replicate all objects that have the same prefix, choose **Limit the scope of this rule using one or more filters**\. This will limit replication to all objects that have names that begin with the string \(for example `pictures`\)\. Enter a prefix in the box\. 
**Note**  
If you enter a prefix that is the name of a folder, you must use **/** \(forward slash\) as the last character \(for example, `pictures/`\)\.
   + To replicate all objects with one or more object tags, select **Add tag** and enter the key value pair in the boxes\. Repeat the procedure to add another tag\. You can combine a prefix and tags\. For more information about object tags, see [Object Tagging](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html) in the *Amazon Simple Storage Service Developer Guide*\.

   The new schema supports prefix and tag filtering and the prioritization of rules\. For more information about the new schema, see [ Replication Configuration Backward Compatibility](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-add-config.html#replication-backward-compat-considerations) in the *Amazon Simple Storage Service Developer Guide*\. The developer guide describes the XML used with the Amazon S3 API that works behind the user interface\. In the developer guide, the new schema is described as *replication configuration XML V2*\.

1. Under **Destination**, you have the following options for setting the replication destination:
   + To replicate to a bucket in your account, select **Choose a bucket in this account** and type or browse for your the destination bucket\. 
   + To replicate to a bucket in a different AWS account, select **Choose a bucket in another account** and enter the destination bucket account ID and type your destination bucket name\. 

     If the destination bucket is in a different account from the source bucket, you must add a bucket policy to the destination bucket to grant the owner of the source bucket account permission to replicate objects in the destination bucket\. For more information, see [Granting permissions when source and destination buckets are owned by different AWS accounts](https://docs.aws.amazon.com/AmazonS3/latest/dev/setting-repl-config-perm-overview.html#setting-repl-config-crossacct) in the *Amazon Simple Storage Service Developer Guide*\.
**Note**  
If versioning is not enabled on the destination bucket, you will get a warning that contains an **Enable versioning** button\. Choose this button to enable versioning on the bucket\.

1. Under **Destination**, you can also set the following options:
   + If you want to enable **Object Ownership** to help standardize ownership of new objects in the destination bucket, choose **Change object ownership to the destination bucket owner**\. For more information about this option, see [Meet compliance requirements using S3 RTC](https://docs.aws.amazon.com/AmazonS3/latest/dev/about-object-ownership.html) in the *Amazon Simple Storage Service Developer Guide*\.
   + If you want to replicate your data into a specific storage class in the destination bucket, choose **Change the storage class for the replicated objects**\. Then choose the storage class that you want to use for the replicated objects in the destination bucket\. If you don't select this option, the storage class for replicated objects is the same class as the original objects\. 
   + If you want to enable delete marker replication in your replication configuration, select **delete marker replication**\. For more information see, [Keep source bucket deletes in sync with delete marker replication](https://docs.aws.amazon.com/AmazonS3/latest/dev/delete-marker-replication.html)\.
   + If you want to enable S3 replication metrics in your replication configuration, select **Replication metrics and events**\. For more information see, [Monitor progress with S3 replication metrics](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-metrics.html)\.
   + If you want to enable S3 Replication Time Control \(S3 RTC\) in your replication configuration, select **S3 Replication Time Control**\. For more information about this option, see [Meet compliance requirements using S3 RTC](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-time-control.html) in the *Amazon Simple Storage Service Developer Guide*\.
**Note**  
When you use S3 RTC or S3 replication metrics, additional fees apply\.

1. To replicate objects in the source bucket that are encrypted with AWS Key Management Service \(AWS KMS\), under **Replication criteria**, select **Replicate objects encrypted with AWS KMS**\. Under **AWS KMS key for encrypting destination objects** are the source keys that you allow replication to use\. All source CMKs are included by default\. You can choose to narrow the CMK selection\. 

   Objects encrypted by AWS KMS CMKs that you do not select are not replicated\. A CMK or a group of CMKs is chosen for you, but you can choose the CMKs if you want\. For information about using AWS KMS with replication, see [Replicating Objects Created with Server\-Side Encryption \(SSE\) Using Encryption Keys Stored in AWS KMS](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-config-for-kms-objects.html) in the *Amazon Simple Storage Service Developer Guide*\.
**Important**  
When you replicate objects that are encrypted with AWS KMS, the AWS KMS request rate doubles in the source Region and increases in the destination Region by the same amount\. These increased call rates to AWS KMS are due to the way that data is re\-encrypted using the customer master key \(CMK\) that you define for the replication destination Region\. AWS KMS has a request rate limit that is per calling account per Region\. For information about the limit defaults, see [AWS KMS Limits \- Requests per Second: Varies](https://docs.aws.amazon.com/kms/latest/developerguide/limits.html#requests-per-second) in the *AWS Key Management Service Developer Guide*\.   
If your current Amazon S3 PUT object request rate during replication is more than half the default AWS KMS rate limit for your account, we recommend that you request an increase to your AWS KMS request rate limit\. To request an increase, create a case in the AWS Support Center at [Contact Us](https://aws.amazon.com/contact-us/)\. For example, suppose that your current PUT object request rate is 1,000 requests per second and you use AWS KMS to encrypt your objects\. In this case, we recommend that you ask AWS Support to increase your AWS KMS rate limit to 2,500 requests per second, in both your source and destination Regions \(if different\), to ensure that there is no throttling by AWS KMS\.   
To see your PUT object request rate in the source bucket, view `PutRequests` in the Amazon CloudWatch request metrics for Amazon S3\. For information about viewing CloudWatch metrics, see [How do I create a request metrics filter for all the objects in my S3 bucket?](configure-metrics.md)

   If you chose to replicate objects encrypted with AWS KMS, enter the Amazon Resource Name \(ARN\) of the AWS KMS CMK to use to encrypt the replicas in the destination bucket\. You can find the ARN for your AWS KMS CMK in the IAM console, under **Encryption keys**\. Or, you can choose a CMK name from the drop\-down list\.

   For more information about creating an AWS KMS CMK, see [Creating Keys](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html) in the *AWS Key Management Service Developer Guide*\.
**Important**  
The Amazon S3 console lists only 100 AWS KMS CMKs per AWS Region\. If you have more than 100 CMKs in the same Region, you can see only the first 100 CMKs in the S3 console\. To use a KMS CMK that is not listed in the console, choose **Custom KMS ARN**, and enter the KMS CMK ARN\.

1. To finish, choose **Save**\.

1. After you save your rule, you can edit, enable, disable, or delete your rule by selecting your rule and choosing **Edit rule**\. 

## Grant the source bucket owner permission to encrypt using the AWS KMS CMK<a name="enable-replication-kms-key-policy"></a>

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