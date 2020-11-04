# How do I delete a request metrics filter?<a name="delete-request-metrics-filter"></a>

In the Amazon S3 console, you can delete a request metrics filter\. When you delete a filter, you are no longer charged for request metrics that use that *specific filter*\. However, you will continue to be charged for any other filter configurations that exist\. When you delete a filter, you can no longer use the filter for request metrics\. Deleting a filter cannot be undone\. 

For more information about creating a request metrics filter, see [How do I create a request metrics filter for all the objects in my S3 bucket?](configure-metrics.md) and [How do I create a request metrics filter that limits scope by object tag or prefix?](configure-metrics-filter.md)

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose your bucket name\.

1. Choose the **Metrics** tab\.

1. Under **Bucket metrics**, choose **View additional charts**\.

1. Choose the **Request metrics** tab\.

1. Choose **Manage filters**\.

1. Choose your filter\.
**Important**  
Deleting a filter cannot be undone\.

1. Choose **Delete**\.

   Amazon S3 deletes your filter\.