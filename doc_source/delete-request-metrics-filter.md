# How do I delete a request metrics filter?<a name="delete-request-metrics-filter"></a>

In the Amazon S3 console, you can delete a request metrics filter\. When you delete a filter, you are no longer charged for request metrics that use that *specific filter*\. However, you will continue to be charged for any other filter configurations that exist\. When you delete a filter, you can no longer use the filter for request metrics\. Deleting a filter cannot be undone\. 

For more information about creating a request metrics filter, see [How do I create a request metrics filter for all the objects in my S3 bucket?](configure-metrics.md) and [How do I create a request metrics filter that limits scope by object tag or prefix?](configure-metrics-filter.md)

## Deleting a request metrics filter \(legacy Amazon S3 console experience\)<a name="delete-rm-filter"></a>

**To delete a filter that limits scope with tags or prefixes**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that contains the objects you want request metrics for\.

1. Choose the **Management** tab, and then choose **Metrics**\.

1. Choose **Requests**\.

1. Under **Filters**, choose the edit icon beside your filter\.
**Important**  
Deleting a filter cannot be undone\.

1. Choose **Delete filter**\.

   Amazon S3 deletes your filter\.

**To delete a filter for all the objects in your bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that contains the objects you want request metrics for\.

1. Choose the **Management** tab, and then choose **Metrics**\.

1. Choose **Requests**\.

1. Choose the edit icon beside the bucket icon\.

1. Clear **Request metrics**\.

   Clearing **Request metrics** also clears **Data transfer metrics**\.

1. Choose **Save**\.

## Deleting a request metrics filter \(new Amazon S3 console experience\)<a name="delete-rm-filter-new"></a>

**Note**  
We are in the process of releasing a new Amazon S3 console experience to customers\. These instructions describe the new experience\. If you don't see the new console now, don't worry\. It will soon be available to all customers\. For instructions using the previous console experience, expand **Deleting a request metrics filter \(legacy Amazon S3 console experience\)** on this page\.

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