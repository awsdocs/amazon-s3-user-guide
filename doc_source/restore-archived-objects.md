# How do I restore an S3 object that has been archived?<a name="restore-archived-objects"></a>

This section explains how to use the Amazon S3 console to restore an object that has been archived to the S3 Glacier, S3 Glacier Deep Archive, S3 Intelligent\-Tiering Archive Access, or S3 Intelligent\-Tiering Deep Archive Access storage classes\. After restoring an object, you can download it from the **Overview** page\. For more information about how all Amazon S3 storage classes compare, see [Storage classes](https://docs.aws.amazon.com/AmazonS3/latest/dev/storage-class-intro.html) in the *Amazon Simple Storage Service Developer Guide*\. 

For detailed information about restoring objects, duration lengths, pricing, and upgrading in\-progress restore speeds, see [Restoring archived objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/restoring-objects.html) in the *Amazon Simple Storage Service Developer Guide*\.

**Topics**
+ [Archive retrieval options](#restore-archived-objects-retrieval-options)
+ [Restoring an archived Amazon S3 object](#restore-archived-objects-how-to)
+ [Upgrade an in\-progress restore](#restore-archived-objects-upgrade)
+ [Checking archive restore status and expiration date](#restore-archived-objects-status)

## Archive retrieval options<a name="restore-archived-objects-retrieval-options"></a>

The following are the available retrieval options when restoring an archived object in Amazon S3: 
+ **`Expedited`** \- *Expedited* retrievals allow you to quickly access your data stored in the S3 Glacier storage class or S3 Intelligent\-Tiering Archive Access tier when occasional urgent requests for a subset of archives are required\. For all but the largest archived objects \(250 MB\+\), data that is accessed using expedited retrievals is typically made available within 1–5 minutes\.
+ **`Standard`** \- *Standard* retrievals allow you to access any of your archived objects within several hours\. This is the default option for retrieval requests that don't specify the retrieval option\. Standard retrievals typically finish within 3–5 hours for objects that are stored in the S3 Glacier storage class or S3 Intelligent\-Tiering Archive Access tier\. They typically finish within 12 hours for objects that are stored in the S3 Glacier Deep Archive or S3 Intelligent\-Tiering Deep Archive Access storage class\. Standard retrievals are free for objects that are stored in S3 Intelligent\-Tiering\.
+ **`Bulk`** \- *Bulk* retrievals are the lowest\-cost retrieval option in Amazon S3 Glacier\. They enable you to retrieve large amounts, even petabytes, of data inexpensively\. Bulk retrievals typically finish within 5–12 hours for objects that are stored in the S3 Glacier storage class or S3 Intelligent\-Tiering Archive Access tier\. They typically finish within 48 hours for objects that are stored in the S3 Glacier Deep Archive storage class or S3 Intelligent\-Tiering Deep Archive Access tier\. Bulk retrievals are free for objects that are stored in S3 Intelligent\-Tiering\.

For more information about retrieval options, provisioned capacity, retrieval speeds, and pricing, see [Restoring archived objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/restoring-objects.html) in the *Amazon Simple Storage Service Developer Guide*\.

## Restoring an archived Amazon S3 object<a name="restore-archived-objects-how-to"></a>

**To restore archived objects**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that contains the objects that you want to restore\.

1. In the **Objects** list, select the object or objects that you want to restore, choose **Actions**, and then choose **Initiate restore**\.

1. If you're restoring from S3 Glacier or S3 Glacier Deep Archive, enter the number of days that you want your archived data to be accessible in the **Initiate restore** dialog box\. 

1. In **Retrieval options**, do one of the following:
   + Choose **Bulk retrieval** or **Standard retrieval**, and then choose **Restore**\. 
   + Choose **Expedited retrieval** \(available only for S3 Glacier or S3 Intelligent\-Tiering Archive Access\)\.

1. Provisioned capacity is only available for objects in S3 Glacier\. If you have provisioned capacity, choose **Restore** to start a provisioned retrieval\. 

   If you have provisioned capacity, all of your expedited retrievals are served by your provisioned capacity\. For more information, see [ Provisioned capacity](https://docs.aws.amazon.com/AmazonS3/latest/dev/restoring-objects.html#restoring-objects-expedited-capacity)\. 
   + If you don't have provisioned capacity and you don't want to buy it, choose **Restore**\. 
   + If you don't have provisioned capacity, but you want to buy it, choose **Add capacity unit**, and then choose **Buy**\. When you get the **Purchase succeeded** message, choose **Restore** to start provisioned retrieval\.

## Upgrade an in\-progress restore<a name="restore-archived-objects-upgrade"></a>

You can upgrade the speed of your restoration while it is in progress\.

**To upgrade an in\-progress restore to a faster tier**

1. Open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that contains the objects that you want to restore\.

1. In the **Objects** list, select one or more of the objects that you are restoring, choose **Actions**, and then choose **Restore from Glacier**\. For information about checking the restoration status of an object, see [Checking archive restore status and expiration date](#restore-archived-objects-status)\. 

1. Choose the tier that you want to upgrade to, and then choose **Restore**\. 

   For information about upgrading to a faster restore tier, see [Restoring archived objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/restoring-objects.html) in the *Amazon Simple Storage Service Developer Guide*\. 
**Note**  
Standard and bulk restores for S3 Intelligent\-Tiering are free of charge\. However, subsequent restore requests called on an object that is already being restored are billed as a GET request\.

## Checking archive restore status and expiration date<a name="restore-archived-objects-status"></a>

To check the progress of the restoration, see the object overview\. For information about the overview, see [How do I see an overview of an object?](view-object-overview.md)

The **Object overview** shows that the restoration is **In progress**\. 

If you're restoring from S3 Glacier or S3 Glacier Deep Archive, the temporary copy of the **Object overview** shows the **Restoration expiry date**\. Amazon S3 will remove the restored copy of your archive on this date\.

Restored objects from S3 Glacier or S3 Glacier Deep Archive are stored only for the number of days that you specify\. If you want a permanent copy of the object, create a copy of it in your Amazon S3 bucket\. 

Amazon S3 calculates the expiry date by adding the number of days that you specify to the time you request to restore the object, and then rounding to the next day at midnight UTC\. This calculation applies to the initial restoration of the object and to any extensions to availability that you request\. For example, if an object was restored on Oct 15, 2012 10:30 AM UTC, and the number of days that you specified is **3**, the object is available until Oct 19, 2012 00:00 UTC\. If, on Oct 16, 2012 11:00 AM UTC, you change the number of days that you want it to be accessible to **1**, Amazon S3 makes the restored object available until Oct 18, 2012 00:00 UTC\.

After restoring an object, you can download it from the **Overview** page\. For more information, see [How do I see an overview of an object?](view-object-overview.md)

### More info<a name="restore-archived-objects-status-moreinfo"></a>
+ [ Restoring archived objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/restoring-objects.html) in the *Amazon S3 Developer Guide*\.
+ [ restore\-object](https://docs.aws.amazon.com/cli/latest/reference/s3api/restore-object.html) in the *AWS CLI Command Reference*\.
+ [Identity and access management in Amazon S3 Glacier](https://docs.aws.amazon.com/amazonglacier/latest/dev/auth-and-access-control.html) in the *Amazon S3 Glacier Developer Guide*\.
+ [How do I create a lifecycle rule for an S3 bucket?](create-lifecycle.md)
+  [How do I undelete a deleted S3 object?](undelete-objects.md)