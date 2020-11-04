# Moving objects<a name="move-object"></a>

In the Amazon S3 console, you can move objects to a bucket or a folder\. 

**To move objects**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. Navigate to the Amazon S3 bucket or folder that contains the objects that you want to move\.

1. Select the check box to the left of the names of the objects that you want to move\.

1. Choose **Actions** and choose **Move** from the list of options that appears\.

   Alternatively, choose **Move** from the options in the upper right\. 

1. To specify the destination path, choose **Browse S3**, navigate to the destination, and select the check box to the left of the destination\. Choose **Choose destination** in the lower right\. 

   Alternatively, enter the destination path\. 

1. If you do *not* have bucket versioning enabled, you might be asked to acknowledge that existing objects with the same name are overwritten\. If this is OK, select the check box and proceed\. If you want to keep all versions of objects in this bucket, select **Enable Bucket Versioning**\. You can also update default encryption and Object Lock properties\.

1. Choose **Move** in the bottom right and Amazon S3 moves your objects to the destination\.

**Note**  
This action creates a copy of all specified objects with updated settings, updates the last\-modified date in the specified location, and adds a delete marker to the original object\. 
When moving folders, wait for the move action to finish before making additional changes in the folders\. 
Objects encrypted with customer\-provided encryption keys \(SSE\-C\) cannot be copied using the S3 console\. To copy objects encrypted with SSE\-C, use the AWS CLI, AWS SDK, or the Amazon S3 REST API\. 
This action updates metadata for bucket versioning, encryption, Object Lock features, and archived objects\. 