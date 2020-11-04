# Deleting objects<a name="delete-objects"></a>

This section explains how to use the Amazon S3 console to delete objects\. Because all objects in your S3 bucket incur storage costs, you should delete objects that you no longer need\. If you are collecting log files, for example, it's a good idea to delete them when they're no longer needed\. You can set up a lifecycle rule to automatically delete objects such as log files\. For more information about lifecycle rules, see [How do I create a lifecycle rule for an S3 bucket?](create-lifecycle.md) in this guide\.

For information about Amazon S3 features and pricing, see [Amazon S3](https://aws.amazon.com/s3/)\.

**To delete objects**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. Navigate to the Amazon S3 bucket or folder that contains the objects that you want to delete\.

1. Select the check box to the left of the names of the objects that you want to delete\.

1. Choose **Actions** and choose **Delete** from the list of options that appears\.

   Alternatively, choose **Delete** from the options in the upper right\. 

1. Enter **delete** if asked to confirm that you want to delete these objects\.

1. Choose **Delete objects** in the bottom right and Amazon S3 deletes the specified objects\.

**Warning**  
Deleting the specified objects cannot be undone\.
This action deletes all specified objects\. When deleting folders, wait for the delete action to finish before adding new objects to the folder\. Otherwise, new objects might be deleted as well\.
Deleting the specified objects cannot be undone\.