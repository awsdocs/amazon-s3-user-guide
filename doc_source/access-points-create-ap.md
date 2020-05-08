# Creating an Amazon S3 access point<a name="access-points-create-ap"></a>

This section explains how to create an Amazon S3 access point using the AWS Management Console\. For information about creating access points using the AWS CLI, AWS SDKs, and the Amazon S3 REST APIs, see [Managing Data Access with Amazon S3 Access Points](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-points.html) in the *Amazon Simple Storage Service Developer Guide*\.

An access point is associated with exactly one Amazon S3 bucket\. Before you begin, make sure that you have created a bucket that you want to use with this access point\. For more information about creating buckets, see [Creating and configuring an S3 bucket](create-configure-bucket.md)\.

**To create an access point**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **S3 buckets** section, select the bucket that you want to attach this access point to\.

1. On the bucket detail page, choose the **Access points** tab\.

1. Choose **Create access point**\.

1. Enter your desired name for the access point in the **Access point name** field\.

1. Choose a **Network access type**\. If you choose **Virtual private cloud \(VPC\)**, enter the **VPC ID** that you want to use with the access point\.

   For more information about network access type for access points, see [Creating Access Points Restricted to a Virtual Private Cloud](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-points.html#access-points-vpc) in the *Amazon Simple Storage Service Developer Guide*\.

1. Select the block public access settings that you want to apply to the access point\. All block public access settings are enabled by default for new access points, and we recommend that you leave all settings enabled unless you know you have a specific need to disable any of them\. Amazon S3 currently doesn't support changing an access point's block public access settings after the access point has been created\.

   For more information about using Amazon S3 Block Public Access with access points, see [Managing Public Access to Access Points](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-points.html#access-points-bpa-settings) in the *Amazon Simple Storage Service Developer Guide*\.

1. \(Optional\) Specify the access point policy\. The console automatically displays the Amazon Resource Name \(ARN\) for the access point, which you can use in the policy\.

1. Choose **Create access point**\.