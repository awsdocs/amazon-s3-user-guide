# How do I restore an S3 object that has been archived?<a name="restore-archived-objects"></a>

This section explains how to use the Amazon S3 console to restore an object that has been archived to the S3 Glacier or S3 Glacier Deep Archive storage classes\. Objects stored in the S3 Glacier or S3 Glacier Deep Archive are not immediately accessible\. To access an object in this class, you must restore a temporary copy of it to its S3 bucket for the duration \(number of days\) that you specify\. For information about the S3 Glacier or S3 Glacier Deep Archive storage classes, see [Storage Classes](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) in the *Amazon Simple Storage Service Developer Guide*\. 

When you restore an archive, you pay for both the archive and the restored copy\. Because there is a storage cost for the copy, restore objects only for the duration you need them\. If you want a permanent copy of the object, create a copy of it in your S3 bucket\. For information about Amazon S3 features and pricing, see [Amazon S3](https://aws.amazon.com/s3/)\.

After restoring an object, you can download it from the **Overview** page\. For more information, see [How do I see an overview of an object?](view-object-overview.md)\.

**Topics**
+ [Archive Retrieval Options](#restore-archived-objects-retrieval-options)
+ [Restoring an Archived S3 Object](#restore-archived-objects-how-to)
+ [Upgrade an In\-Progress Restore](#restore-archived-objects-upgrade)
+ [Checking Archive Restore Status and Expiration Date](#restore-archived-objects-status)

## Archive Retrieval Options<a name="restore-archived-objects-retrieval-options"></a>

The following are the available retrieval options when restoring an archived object: 
+ **`Expedited`** \- Expedited retrievals allow you to quickly access your data stored in the S3 Glacier storage class when occasional urgent requests for a subset of archives are required\. For all but the largest archived objects \(250 MB\+\), data accessed using Expedited retrievals is typically made available within 1–5 minutes\. Provisioned capacity ensures that retrieval capacity for Expedited retrievals is available when you need it\. For more information, see [ Provisioned Capacity](https://docs.aws.amazon.com/AmazonS3/latest/dev/restoring-objects.html#restoring-objects-expedited-capacity)\. Expedited retrievals and provisioned capacity are not available for objects stored in the S3 Glacier Deep Archive storage class\.
+ **`Standard`** \- Standard retrievals allow you to access any of your archived objects within several hours\. This is the default option for the S3 Glacier and S3 Glacier Deep Archive retrieval requests that do not specify the retrieval option\. Standard retrievals typically finish within 3–5 hours for objects stored in the S3 Glacier storage class\. They typically finish within 12 hours for objects stored in the S3 Glacier Deep Archive storage class\. 
+ **`Bulk`** \- Bulk retrievals are the lowest\-cost retrieval option in Amazon S3 Glacier, enabling you to retrieve large amounts, even petabytes, of data inexpensively\. Bulk retrievals typically finish within 5–12 hours for objects stored in the S3 Glacier storage class\. They typically finish within 48 hours for objects stored in the S3 Glacier Deep Archive storage class\.

For more information about retrieval options, see [Restoring Archived Objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/restoring-objects.html) in the *Amazon Simple Storage Service Developer Guide*\.

## Restoring an Archived S3 Object<a name="restore-archived-objects-how-to"></a>

This topic explains how to use the Amazon S3 console to restore an object that has been archived to the S3 Glacier or S3 Glacier Deep Archive storage classes\. \(The console uses the names Glacier and Glacier Deep Archive for these storage classes\.\)

**To restore archived S3 objects**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that contains the objects that you want to restore\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. In the **Name** list, select the object or objects that you want to restore, choose **Actions**, and then choose **Restore**\.  
![\[Console screenshot showing how to select and restore archived object.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/restore-archived-objects.png)

1. In the **Initiate restore** dialog box, type the number of days that you want your archived data to be accessible\. 

1. Choose one of the following retrieval options from the **Retrieval options** menu\.
   + Choose **Bulk retrieval** or **Standard retrieval**, and then choose **Restore**\. 
   + Choose **Expedited retrieval** \(available only for the Glacier storage class\)\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/initiate-restore.png)

1. Provisioned capacity is only available for the Glacier storage class\. If you have provisioned capacity, choose **Restore** to start a provisioned retrieval\. If you have provisioned capacity, all of your expedited retrievals are served by your provisioned capacity\. For more information about provisioned capacity, see [ Provisioned Capacity](https://docs.aws.amazon.com/AmazonS3/latest/dev/restoring-objects.html#restoring-objects-expedited-capacity)\. 
   + If you don't have provisioned capacity and you don't want to buy it, choose **Restore**\. 
   + If you don't have provisioned capacity, but you want to buy it, choose **Add capacity unit**, and then choose **Buy**\. When you get the **Purchase succeeded** message, choose **Restore** to start provisioned retrieval\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/initiate-expedited-restore.png)

## Upgrade an In\-Progress Restore<a name="restore-archived-objects-upgrade"></a>

You can upgrade the speed of your restoration while it is in progress\.

**To upgrade an in\-progress restore to a faster tier**

1. In the **Name** list, select one or more of the objects that you are restoring, choose **Actions**, and then choose **Restore from Glacier**\. For information about checking the restoration status of an object, see [Checking Archive Restore Status and Expiration Date](#restore-archived-objects-status)\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/restore-archived-objects.png)

1. Choose the tier that you want to upgrade to and then choose **Restore**\. For more information about upgrading to a faster restore tier, see see [Restoring Archived Objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/restoring-objects.html) in the *Amazon Simple Storage Service Developer Guide*\. 

## Checking Archive Restore Status and Expiration Date<a name="restore-archived-objects-status"></a>

To check the progress of the restoration, see the object overview panel\. For information about the overview panel, see [How do I see an overview of an object?](view-object-overview.md)\. 

The **Overview** section shows that restoration is **In progress**\. 

When the temporary copy of the object is available, the object's **Overview** section shows the **Restoration expiry date**\. This is when Amazon S3 will remove the restored copy of your archive\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/glacier-restore-statexpire-date.png)

Restored objects are stored only for the number of days that you specify\. If you want a permanent copy of the object, create a copy of it in your Amazon S3 bucket\. 

Amazon S3 calculates the expiry date by adding the number of days that you specify to the time you request to restore the object, and then rounding to the next day at midnight UTC\. This calculation applies to the initial restoration of the object and to any extensions to availability that you request\. For example, if an object was restored on 10/15/2012 10:30 AM UTC and the number of days that you specified is 3, then the object is available until 10/19/2012 00:00 UTC\. If, on 10/16/2012 11:00 AM UTC you change the number of days that you want it to be accessible to 1, then Amazon S3 makes the restored object available until 10/18/2012 00:00 UTC\.

After restoring an object, you can download it from the **Overview** page\. For more information, see [How do I see an overview of an object?](view-object-overview.md)\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/object-overview-download-short.png)

### More Info<a name="restore-archived-objects-status-moreinfo"></a>
+ [ Restoring Archived Objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/restoring-objects.html) in the Amazon S3 Developer Guide\.
+ [ restore\-object](https://docs.aws.amazon.com/cli/latest/reference/s3api/restore-object.html) in the AWS CLI Command Reference\.
+ [Identity and Access Management in Amazon S3 Glacier](https://docs.aws.amazon.com/amazonglacier/latest/dev/auth-and-access-control.html) in the S3 Glacier Developer Guide\.
+ [How do I create a lifecycle policy for an S3 Bucket?](create-lifecycle.md)
+  [How do I undelete a deleted S3 object?](undelete-objects.md)