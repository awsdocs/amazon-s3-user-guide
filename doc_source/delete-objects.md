# How do I delete objects from an S3 bucket?<a name="delete-objects"></a>

This section explains how to use the Amazon S3 console to delete objects\. Because all objects in your S3 bucket incur storage costs, you should delete objects that you no longer need\. If you are collecting log files, for example, it's a good idea to delete them when they're no longer needed\. You can set up a lifecycle rule to automatically delete objects such as log files\.

For information about Amazon S3 features and pricing, see [Amazon S3](https://aws.amazon.com/s3/)\.

**To delete objects from an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to delete an object from\.

1. You can delete objects from an S3 bucket in any of the following ways:
   + In the **Name** list, select the check box next to the objects and folders that you want to delete, choose **Actions**, and then choose **Delete** from the drop\-down menu\.

     In the **Delete objects** dialog box, verify that the name\(s\) of the object\(s\) and/or folder\(s\) you selected for deletion are listed and then choose **Delete**\.
   + Or, choose the name of the object that you want to delete, choose **Latest version**, and then choose the **trash can** icon\.

## More info<a name="delete-objects-more-info"></a>
+  [How do I undelete a deleted S3 object?](undelete-objects.md)
+ [How do I create a lifecycle policy for an S3 Bucket?](create-lifecycle.md)