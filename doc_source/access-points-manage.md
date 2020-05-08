# Managing and using Amazon S3 access points<a name="access-points-manage"></a>

This section explains how to manage and use your Amazon S3 access points using the AWS Management Console\. Each access point is associated with a single Amazon S3 bucket\. Before you begin, navigate to the list of your access points for a bucket as described in the following procedure\.

**To find a list of access points for a bucket**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **S3 buckets** section, select the bucket whose access points you want to manage\.

1. On the bucket detail page, choose the **Access points** tab\.

From the **Access points** tab, you can view an access point's configuration details, edit an access point's policy, use an access point to access your bucket, or delete an access point\. The following procedures explain how to perform each of these tasks\.

**To view access point configuration details**

1. Navigate to the **Access points** tab for your bucket\.

1. Locate the access point whose configuration you want to view\. You can browse for the access point in the access point list, or you can search for a specific access point using the **Search by name** field\.

1. Choose the name of the access point whose configuration you want to view\.
**Note**  
To view an access point's configuration, choose \(click on\) the name of the access point, not the option button next to the access point name\.

**To edit an access point policy**

1. Navigate to the **Access points** tab for your bucket\.

1. Select the option button next to the name of the access point whose policy you want to edit\.

1. Choose **Edit access point policy**\.

1. Enter the policy in the text field\. The console automatically displays the Amazon Resource Name \(ARN\) for the access point, which you can use in the policy\. You can also choose **Policy generator** to use the AWS Policy Generator to help construct the policy\.

1. Choose **Save**\.

**To use an access point to access your bucket**

1. Navigate to the **Access points** tab for your bucket\.

1. Select the option button next to the name of the access point you want to use\.

1. Choose **Use this access point**\.

1. The console displays a label above the name of your bucket that shows the access point that you're currently using\. While you're using the access point, you can only perform the object operations that are allowed by the access point permissions\.
**Note**  
The console view always shows all objects in the bucket\. Using an access point as described in this procedure restricts the operations you can perform on those objects, but not whether you can see that they exist in the bucket\.

1. To exit the access point view of your bucket, choose **Exit access point**\.

**Note**  
The S3 Management Console doesn't support using virtual private cloud \(VPC\) access points to access bucket resources\. To access bucket resources from a VPC access point, use the AWS CLI, AWS SDKs, or Amazon S3 REST APIs\.

**To delete an access point**

1. Navigate to the **Access points** tab for your bucket\.

1. Select the option button next to the name of the access point that you want to delete\.

1. Choose **Delete**\.

1. Confirm that you want to delete your access point by entering its name in the text field that appears, and choose **Confirm**\.