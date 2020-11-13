# How do I create a lifecycle rule for an S3 bucket?<a name="create-lifecycle"></a>

You can use lifecycle rules to define actions that you want Amazon S3 to take during an object's lifetime \(for example, transition objects to another storage class, archive them, or delete them after a specified period of time\)\.

You can define a lifecycle rules for all objects or a subset of objects in the bucket by using a shared prefix \(objects names that begin with a common string\) or a tag\. 

Using a lifecycle rule you can define actions specific to current and non\-current object versions\. For more information, see [Object Lifecycle Management](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html) and [Object Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html) and [Using Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html) in the *Amazon Simple Storage Service Developer Guide*\.

**To create a lifecycle rule**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket that you want to create a lifecycle rule for\.

1. Choose the **Management** tab, and choose **Create lifecycle rule**\.

1. In **Lifecycle rule name**, enter a name for your rule\. 

   The name must be unique within the bucket\. 

1. Choose the scope of the lifecycle rule: 
   + To apply this lifecycle rule to *all objects with a specific prefix or tag*, choose **Limit the scope to specific prefixes or tags**\.
     + To limit the scope by prefix, in **Prefix**, enter the prefix\. 
     + To limit the scope by tag, choose **Add tag**, and enter the tag key and value\.

       For more information about object name prefixes, see [Object Keys](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html#object-keys) in the *Amazon Simple Storage Service Developer Guide*\. For more information about object tags, see [Object Tagging](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html) in the *Amazon Simple Storage Service Developer Guide*\. 
   + To apply this lifecycle rule to *all objects in the bucket*, choose **This rule applies to *all* objects in the bucket**, and choose **I acknowledge that this rule applies to all objects in the bucket**\.

1. Under **Lifecycle rule actions**, choose the actions that you want your lifecycle rule to perform:
   + Transition *current* versions of objects between storage classes
   + Transition *previous* versions of objects between storage classes
   + Expire *current* versions of objects
   + Permanently delete *previous* versions of objects
   + Delete expired delete markers or incomplete multipart uploads 

   Depending on the actions that you choose, different options appear\.

1. To transition *current* versions of objects between storage classes, under **Transition current versions of objects between storage classes**:

   1. In **Storage class transitions**, choose the storage class to transition to:
      + Standard\-IA
      + Intelligent\-Tiering
      + One Zone\-IA
      + Glacier
      + Glacier Deep Archive

   1. In **Days after object creation**, enter the number of days after creation to transition the object\.

   For more information about storage classes, see [Storage Classes](https://docs.aws.amazon.com/AmazonS3/latest/dev/storage-class-intro.html) in the *Amazon Simple Storage Service Developer Guide*\. You can define transitions for current or previous object versions or for both current and previous versions\. Versioning enables you to keep multiple versions of an object in one bucket\. For more information about versioning, see [How do I enable or suspend versioning for an S3 bucket?](enable-versioning.md)\.
**Important**  
When you choose the Glacier or Glacier Deep Archive storage class, your objects remain in Amazon S3\. You cannot access them directly through the separate Amazon S3 Glacier service\. For more information, see [Transitioning Objects Using Amazon S3 Lifecycle](https://docs.aws.amazon.com/AmazonS3/latest/dev/lifecycle-transition-general-considerations.html)\. 

1. To transition *non\-current* versions of objects between storage classes, under **Transition non\-current versions of objects between storage classes**:

   1. In **Storage class transitions**, choose the storage class to transition to:
      + Standard\-IA
      + Intelligent\-Tiering
      + One Zone\-IA
      + Glacier
      + Glacier Deep Archive

   1. In **Days after object becomes non\-current**, enter the number of days after creation to transition the object\.

1. To expire *current* versions of objects, under **Expire previous versions of objects**, in **Number of days after object creation**, enter the number of days\.
**Important**  
In a non\-versioned bucket the expiration action results in Amazon S3 permanently removing the object\. For more information about lifecycle actions, see [Elements to describe lifecycle actions](https://docs.aws.amazon.com/AmazonS3/latest/dev/intro-lifecycle-rules.html#intro-lifecycle-rules-actions) in the *Amazon Simple Storage Service Developer Guide*\.

1. To permanently delete previous versions of objects, under **Permanently delete previous versions of objects**, in **Number of days after objects become previous versions**, enter the number of days\.

1. Under **Delete expired delete markers or incomplete multipart uploads**, choose **Delete expired object delete markers** and **Delete incomplete multipart uploads**\. Then, enter the number of days after the multipart upload initiation that you want to end and clean up incomplete multipart uploads\.

   For more information about multipart uploads, see [Multipart Upload Overview](https://docs.aws.amazon.com/AmazonS3/latest/dev/mpuoverview.html) in the Amazon Simple Storage Service Developer Guide\.

1. Choose **Create rule**\.

   If the rule does not contain any errors, Amazon S3 enables it, and you can see it on the **Management** tab under **Lifecycle rules**\.

For information about CloudFormation templates and examples, see [Working with AWS CloudFormation templates](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-guide.html) and [AWS::S3::Bucket](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-s3-bucket.html#aws-properties-s3-bucket--examples) in the *AWS CloudFormation User Guide*\.