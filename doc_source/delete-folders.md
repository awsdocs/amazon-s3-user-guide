# How do I delete folders from an S3 bucket?<a name="delete-folders"></a>

This section explains how to use the Amazon S3 console to delete folders from an S3 bucket\. 

For information about Amazon S3 features and pricing, see [Amazon S3](https://aws.amazon.com/s3/)\.

**To delete folders from an S3 bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that you want to delete folders from\.

1. In the **Name** list, select the check box next to the folders and objects that you want to delete, choose **Actions**, and then choose **Delete**\.

1. On the **Delete objects** page, verify that the names of the folders you selected for deletion are listed\. Enter **delete** in the box provided and click **Delete objects**\.

**Warning**  
This action deletes all specified objects\. When deleting folders, wait for the delete action to finish before adding new objects to the folder\. Otherwise, new objects might be deleted as well\.

## Related topics<a name="delete-folders-related-topics"></a>
+ [Deleting objects](delete-objects.md)