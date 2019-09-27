# How Do I Configure Amazon S3 Inventory?<a name="configure-inventory"></a>

Amazon S3 inventory provides a flat file list of your objects and metadata, which is a scheduled alternative to the Amazon S3 synchronous `List` API operation\. Amazon S3 inventory provides comma\-separated values \(CSV\) or [Apache optimized row columnar \(ORC\)](https://orc.apache.org/) or[ Apache Parquet \(Parquet\) ](https://parquet.apache.org/)output files that list your objects and their corresponding metadata on a daily or weekly basis for an S3 bucket or for objects that share a prefix \(objects that have names that begin with the same string\)\. For more information, see [Amazon S3 Inventory](https://docs.aws.amazon.com/AmazonS3/latest/dev/storage-inventory.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To configure inventory**
**Note**  
It may take up to 48 hours to deliver the first report\.

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket for which you want to configure Amazon S3 inventory\.  
![\[Screenshot of the bucket name list with a bucket name highlighted.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose the **Management** tab, and then choose **Inventory**\.

1. Choose **Add new**\.

1. Type a name for the inventory and set it up as follows:
   + Optionally, add a prefix for your filter to inventory only objects whose names begin with the same string\.
   + Choose the destination bucket where you want reports to be saved\. The destination bucket must be in the same AWS Region as the bucket for which you are setting up the inventory\. The destination bucket can be in a different AWS account\. 
   + Optionally, choose a prefix for the destination bucket\.
   + Choose how frequently to generate the inventory\.  
![\[Screenshot showing the boxes to complete when setting up a new inventory.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/inventory-enter-data.png)

1. Under **Advanced settings**, you can set the following:

   1.  Choose either the CSV, ORC, or Parquet output file format for your inventory\. For more information about these formats, see [Amazon S3 Inventory](https://docs.aws.amazon.com/AmazonS3/latest/dev/storage-inventory.html) in the *Amazon Simple Storage Service Developer Guide*\.   
![\[Advanced settings screen with include only current versions selected\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/inventory-enter-data-advanced.png)

   1. To include all versions of the objects in the inventory, choose **Include all versions** in the **Object versions** list\. By default, the inventory includes only the current versions of the objects\.

   1. For **Optional fields**, select one or more of the following to add to the inventory report:
      + **Size** – Object size in bytes\.
      + **Last modified date** – The object creation date or the last modified date, whichever is the latest\.
      + **Storage class** – The storage class used for storing the object\. 
      + **ETag** – The entity tag is a hash of the object\. The ETag reflects changes only to the contents of an object, and not its metadata\. The ETag may or may not be an MD5 digest of the object data\. Whether it is depends on how the object was created and how it is encrypted\.
      +  **Multipart upload** – Specifies that the object was uploaded as a multipart upload\. For more information, see [Multipart Upload Overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/mpuoverview.html) in the *Amazon Simple Storage Service Developer Guide*\.
      + **Replication status** – The replication status of the object\. For more information, see [How Do I Add a Replication Rule to an S3 Bucket?](enable-replication.md)\.
      + **Encryption status** – The server\-side encryption used to encrypt the object\. For more information, see [Protecting Data Using Server\-Side Encryption](https://docs.aws.amazon.com/AmazonS3/latest/dev/serv-side-encryption.html) in the *Amazon Simple Storage Service Developer Guide*\.
      + **Object lock configurations** – The object lock status of the object, including the following settings: 
        + **Retention mode** – The level of protection applied to the object, either *Governance* or *Compliance*\.
        + **Retain until date** – The date until which the locked object cannot be deleted\.
        + **Legal hold status** – The legal hold status of the locked object\. 

        For information about object lock, see [Amazon S3 Object Lock Overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html) in the *Amazon Simple Storage Service Developer Guide*\.

      For more information about the contents of an inventory report, see [ What's Included in an Amazon S3 Inventory?](https://docs.aws.amazon.com/AmazonS3/latest/dev/storage-inventory.html#storage-inventory-contents) in the *Amazon Simple Storage Service Developer Guide*\.

   1. For **Encryption**, choose a server\-side encryption option to encrypt the inventory report, or choose **None**:
      + **None** – Do not encrypt the inventory report\.
      + **AES\-256** – Encrypt the inventory report using server\-side encryption with Amazon S3\-managed keys \(SSE\-S3\)\. Amazon S3 server\-side encryption uses 256\-bit Advanced Encryption Standard \(AES\-256\)\. For more information, see [Amazon S3\-Managed Encryption Keys \(SSE\-S3\)](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingServerSideEncryption.html) in the *Amazon Simple Storage Service Developer Guide*\. 
      + **AWS\-KMS** – Encrypt the report using server\-side encryption with AWS KMS\-managed keys \(SSE\-KMS\)\. For more information, see [AWS KMS–Managed Keys \(SSE\-KMS\)](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingKMSEncryption.html) in the *Amazon Simple Storage Service Developer Guide*\. 
**Note**  
To encrypt the inventory list file with SSE\-KMS, you must grant Amazon S3 permission to use the AWS KMS key\. For instructions, see [Grant Amazon S3 Permission to Encrypt Using Your AWS KMS Key](#configure-inventory-kms-key-policy)\.

1. Choose **Save**\.

## Destination Bucket Policy<a name="configure-inventory-destination-bucket-policy"></a>

Amazon S3 creates a bucket policy on the destination bucket that grants Amazon S3 write permission\. This allows Amazon S3 to write data for the inventory reports to the bucket\. 

If an error occurs when you try to create the bucket policy, you are given instructions on how to fix it\. For example, if you choose a destination bucket in another AWS account and don't have permissions to read and write to the bucket policy, you see the following message\. 

![\[A message showing that inventory is successfully saved and another showing a bucket policy error.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/inventory-bucket-policy.png)

In this case, the destination bucket owner must add the displayed bucket policy to the destination bucket\. If the policy is not added to the destination bucket, you won’t get an inventory report because Amazon S3 doesn’t have permission to write to the destination bucket\. If the source bucket is owned by a different account than that of the current user, the correct account ID of the source bucket must be substituted in the policy\.

For more information, see [Amazon S3 Inventory](https://docs.aws.amazon.com/AmazonS3/latest/dev/storage-inventory.html) in the *Amazon Simple Storage Service Developer Guide*\.

## Grant Amazon S3 Permission to Encrypt Using Your AWS KMS Key<a name="configure-inventory-kms-key-policy"></a>

You must grant Amazon S3 permission to encrypt using your AWS KMS key with a key policy\. The following procedure describes how to use the AWS Identity and Access Management \(IAM\) console to modify the key policy for the AWS KMS customer master key \(CMK\) that is being used to encrypt the inventory file\.

**To grant permissions to encrypt using your AWS KMS key**

1. Sign in to the AWS Management Console using the AWS account that owns the AWS KMS CMK\. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the left navigation pane, choose **Encryption keys**\.

1. For **Region**, choose the appropriate AWS Region\. Do not use the region selector in the navigation bar \(upper\-right corner\)\.

1. Choose the alias of the CMK that you want to encrypt inventory with\.

1. In the **Key Policy** section of the page, choose **Switch to policy view**\.

1. Using the **Key Policy** editor, insert following key policy into the existing policy and then choose **Save Changes**\. You might want to copy the policy to the end of the existing policy\. 

   ```
   {
       "Sid": "Allow Amazon S3 use of the key",
       "Effect": "Allow",
       "Principal": {
           "Service": "s3.amazonaws.com"
       },
       "Action": [
           "kms:GenerateDataKey*"
       ],
       "Resource": "*"
   }
   ```

For more information about creating and editing AWS KMS CMKs, see [Getting Started](https://docs.aws.amazon.com/kms/latest/developerguide/getting-started.html) in the *AWS Key Management Service Developer Guide*\. 

**More Info**  
 [Storage Management](storage-management.md)