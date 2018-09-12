# How Do I Restore an S3 Object That Has Been Archived to Amazon Glacier?<a name="restore-archived-objects"></a>

This section explains how to use the Amazon S3 console to restore an object that has been archived by using the `Glacier` storage class\. Objects in the `Glacier` storage class are not immediately accessible\. To access an object in this class, you must restore a temporary copy of it to its S3 bucket\. You can access objects that have been archived to Amazon Glacier only by using Amazon S3\. You can't use the Amazon Glacier console, AWS command line interface \(CLI\), or APIs to see the S3 archived objects\. For information about when to use the `Glacier` storage class for objects, see [Storage Classes](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) and [Object Lifecycle Management](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) in the *Amazon Simple Storage Service Developer Guide*\. 

Amazon Glacier charges a retrieval fee for retrieving objects stored with the `Glacier` storage class\. For retrieval pricing information, see [Amazon Glacier Pricing](https://aws.amazon.com/glacier/pricing/)\. 

When you restore an archive, you pay for both the archive and the restored copy\. Because there is a storage cost for the copy, restore objects only for the duration you need them\. If you want a permanent copy of the object, create a copy of it in your S3 bucket\. For information about Amazon S3 features and pricing, see [Amazon S3](https://aws.amazon.com/s3/)\.

After restoring an object, you can download it from the **Overview** page\. For more information, see [How Do I See an Overview of an Object?](view-object-overview.md)\.

**Topics**
+ [Archive Retrieval Options](#restore-archived-objects-retrieval-options)
+ [Restoring an Archived S3 Object](#restore-archived-objects-how-to)
+ [Checking Archive Restore Status and Expiration Date](#restore-archived-objects-status)

## Archive Retrieval Options<a name="restore-archived-objects-retrieval-options"></a>

You restore archived objects using one of the following retrieval types: 
+ **Expedited retrieval** – Expedited retrievals typically retrieve objects within 1–5 minutes\. There are two types of Expedited retrievals: On\-Demand and Provisioned\. 
  +  **On\-Demand** – If you don't need a guarantee that your expedited retrieval requests will be immediately successful, and you don't want to purchase provisioned capacity, use On\-Demand expedited retrievals\. Amazon S3 processes On\-Demand expedited retrieval requests the vast majority of the time\. It fails to process them only in rare situations where there is an unusually high retrieval demand\. In that case, repeat the request\.
  +  **Provisioned** – If you need to guarantee that your expedited retrieval requests are processed immediately and you have or are willing to purchase provisioned capacity, use Provisioned expedited retrievals\. After purchasing provisioned capacity, all of your expedited retrievals are served by this capacity\. For pricing information on provisioned capacity, see [Amazon Glacier Pricing](https://aws.amazon.com/glacier/pricing/)\. 
+ **Standard retrieval** – Standard retrievals allow you to access your archived objects within several hours \(typically within 3–5 hours\)\.
+ **Bulk retrieval** – Bulk retrievals are Amazon Glacier’s lowest\-cost retrieval option\. With bulk retrieval, you can retrieve large amounts, even petabytes, of data inexpensively in a day\. Bulk retrievals typically are complete within 5–12 hours\.

For more information about retrieval options, see [ Restoring Archived Objects](http://docs.aws.amazon.com/AmazonS3/latest/dev/restoring-objects.html) in the *Amazon Simple Storage Service Developer Guide*\.

## Restoring an Archived S3 Object<a name="restore-archived-objects-how-to"></a>

This topic explains how to use the Amazon S3 console to restore an object that has been archived to Amazon Glacier\. 

**To restore archived S3 objects**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that contains the objects that you want to restore\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. In the **Name** list, select the objects that you want to restore, choose **More**, and then choose **Initiate restore**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/restore-archived-objects.png)

1. In the **Initiate restore** dialog box, type the number of days that you want your archived data to be accessible\. 

1. Choose one of the following retrieval options from the **Retrieval options** menu\.
   + Choose **Bulk retrieval** or **Standard retrieval**, and then choose **Restore**\. 
   + Choose **Expedited retrieval**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/initiate-restore.png)

1. If you have provisioned capacity, choose **Restore** to start a provisioned retrieval\. If you have provisioned capacity, all of your expedited retrievals are served by your provisioned capacity\. For more information about provisioned capacity, see [Archive Retrieval Options](#restore-archived-objects-retrieval-options)\. 
   + If you don't have provisioned capacity and you don't want to buy it, choose **Restore** to start an On\-Demand retrieval\. 
   + If you don't have provisioned capacity, but you want to buy it, choose **Add capacity unit**, and then choose **Buy**\. When you get the **Purchase succeeded** message, choose **Restore** to start provisioned retrieval\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/initiate-expedited-restore.png)

## Checking Archive Restore Status and Expiration Date<a name="restore-archived-objects-status"></a>

To check the progress of the restoration, see the object overview panel\. For information about the overview panel, see [How Do I See an Overview of an Object?](view-object-overview.md)\. 

The **Properties** section shows that restoration is **In progress**\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/glacier-restore-in-progress.png)

When the temporary copy of the object is available, the object's **Properties** section shows the **Restoration expiry date**\. This is when Amazon S3 will remove the restored copy of your archive\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/glacier-restore-expire-date.png)

Restored objects are stored only for the number of days that you specify\. If you want a permanent copy of the object, create a copy of it in your Amazon S3 bucket\. 

Amazon S3 calculates the expiry date by adding the number of days that you specify to the time you request to restore the object, and then rounding to the next day at midnight UTC\. This calculation applies to the initial restoration of the object and to any extensions to availability that you request\. For example, if an object was restored on 10/15/2012 10:30 AM UTC and the number of days that you specified is 3, then the object is available until 10/19/2012 00:00 UTC\. If, on 10/16/2012 11:00 AM UTC you change the number of days that you want it to be accessible to 1, then Amazon S3 makes the restored object available until 10/18/2012 00:00 UTC\.

After restoring an object, you can download it from the **Overview** page\. For more information, see [How Do I See an Overview of an Object?](view-object-overview.md)\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-overview-download-short.png)

### More Info<a name="restore-archived-objects-status-moreinfo"></a>
+ [How Do I Create a Lifecycle Policy for an S3 Bucket?](create-lifecycle.md)
+  [How Do I Undelete a Deleted S3 Object?](undelete-objects.md)