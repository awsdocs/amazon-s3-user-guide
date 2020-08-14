# How do I upload files and folders to an S3 bucket?<a name="upload-objects"></a>

This topic explains how to use the AWS Management Console to upload one or more files or entire folders to an Amazon S3 bucket\. Before you can upload files and folders to an Amazon S3 bucket, you need write permissions for the bucket\. For more information about access permissions, see [Setting bucket and object access permissions](set-permissions.md)\. For information about uploading files programmatically, see [Uploading Objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/UploadingObjects.html) in the *Amazon Simple Storage Service Developer Guide*\. 

When you upload a file to Amazon S3, it is stored as an S3 object\. Objects consist of the file data and metadata that describes the object\. You can have an unlimited number of objects in a bucket\.

You can upload any file type—images, backups, data, movies, etc\.—into an S3 bucket\. The maximum size of a file that you can upload by using the Amazon S3 console is 160 GB\. To upload a file larger than 160 GB, use the AWS CLI, AWS SDK, or Amazon S3 REST API\. For more information, see [Uploading Objects](https://docs.aws.amazon.com/AmazonS3/latest/dev/UploadingObjects.html) in the *Amazon Simple Storage Service Developer Guide*\. 

**Note**  
To upload *folders*, you must drag and drop them\. To upload *files*, you can drag and drop or point and click\. Drag and drop functionality is supported only for Chrome and Firefox browsers\. 

For information about which Chrome and Firefox browser versions are supported, see [What browsers are supported for use with the AWS Management Console?](https://aws.amazon.com/premiumsupport/knowledge-center/browsers-management-console/)\. 

When you upload a folder, Amazon S3 uploads all of the files and subfolders from the specified folder to your bucket\. It then assigns an object key name that is a combination of the uploaded file name and the folder name\. For example, if you upload a folder called `/images` that contains two files, `sample1.jpg` and `sample2.jpg`, Amazon S3 uploads the files and then assigns the corresponding key names, `images/sample1.jpg` and `images/sample2.jpg`\. The key names include the folder name as a prefix\. The Amazon S3 console displays only the part of the key name that follows the last “/”\. For example, within an images folder the `images/sample1.jpg` and `images/sample2.jpg` objects are displayed as `sample1.jpg` and a `sample2.jpg`\.

If you upload individual files and you have a folder open in the Amazon S3 console, when Amazon S3 uploads the files, it includes the name of the open folder as the prefix of the key names\. For example, if you have a folder named `backup` open in the Amazon S3 console and you upload a file named `sample1.jpg`, the key name is `backup/sample1.jpg`\. However, the object is displayed in the console as `sample1.jpg` in the `backup` folder\.

If you upload individual files and you do not have a folder open in the Amazon S3 console, when Amazon S3 uploads the files, it assigns only the file name as the key name\. For example, if you upload a file named `sample1.jpg`, the key name is `sample1.jpg`\. For more information on key names, see [Object Key and Metadata](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html) in the *Amazon Simple Storage Service Developer Guide*\.

If you upload an object with a key name that already exists in a versioning\-enabled bucket, Amazon S3 creates another version of the object instead of replacing the existing object\. For more information about versioning, see [How do I enable or suspend versioning for an S3 bucket?](enable-versioning.md)\.

**Topics**
+ [Uploading Files and Folders by Using Drag and Drop](#upload-objects-by-drag-and-drop)
+ [Uploading Files by Pointing and Clicking](#upload-objects-by-file-selection)
+ [More Info](#upload-objects-moreinfo)

## Uploading Files and Folders by Using Drag and Drop<a name="upload-objects-by-drag-and-drop"></a>

If you are using the Chrome or Firefox browsers, you can choose the folders and files to upload, and then drag and drop them into the destination bucket\. Dragging and dropping is the *only* way that you can upload folders\.

**To upload folders and files to an S3 bucket by using drag and drop**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to upload your folders or files to\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. In a window other than the console window, select the files and folders that you want to upload\. Then drag and drop your selections into the console window that lists the objects in the destination bucket\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/upload-drag-drop.png)

   The files you chose are listed in the **Upload** dialog box\.

1. In the **Upload** dialog box, do one of the following: 

   1. Drag and drop more files and folders to the console window that displays the **Upload** dialog box\. To add more files, you can also choose **Add more files**\. This option works *only* for files, not folders\.

   1. To immediately upload the listed files and folders without granting or removing permissions for specific users or setting public permissions for all of the files that you're uploading, choose **Upload**\. For information about object access permissions, see [How do I set permissions on an object?](set-object-permissions.md)\. 

   1. To set permissions or properties for the files that you are uploading, choose **Next**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/upload-display-files-and-folders.png)

1. On the **Set Permissions** page, under **Manage users** you can change the permissions for the AWS account owner\. The *owner* refers to the AWS account root user, and not an AWS Identity and Access Management \(IAM\) user\. For more information about the root user, see [The AWS Account Root User](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html)\. 

   Choose **Add account** to grant access to another AWS account\. For more information about granting permissions to another AWS account, see [How do I set ACL bucket permissions?](set-bucket-permissions.md)\.

   Under **Manage public permissions** you can grant read access to your objects to the general public \(everyone in the world\), for all of the files that you're uploading\. Granting public read access is applicable to a small subset of use cases such as when buckets are used for websites\. We recommend that you do not change the default setting of **Do not grant public read access to this object\(s\)**\. You can always make changes to object permissions after you upload the object\. For information about object access permissions, see [How do I set permissions on an object?](set-object-permissions.md)\. 

   When you're done configuring permissions, choose **Next**\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/upload-set-permissions.png)

1. On the **Set Properties** page, choose the storage class and encryption method to use for the files that you are uploading\. You can also add or modify metadata\. 

   1. Choose a storage class for the files you're uploading\. For more information about storage classes, see [Storage Classes](https://docs.aws.amazon.com/AmazonS3/latest/dev/storage-class-intro.html) in the *Amazon Simple Storage Service Developer Guide*\.  
![\[Console screenshot showing the upload set properties dialog.\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/upload-set-properties.png)

   1. Choose the type of encryption for the files that you're uploading\. If you don't want to encrypt them, choose **None**\. 

      1. To encrypt the uploaded files using keys that are managed by Amazon S3, choose **Amazon S3 master\-key**\. For more information, see [Protecting Data with Amazon S3\-Managed Encryption Keys Classes](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingServerSideEncryption.html) in the *Amazon Simple Storage Service Developer Guide*\.

      1. To encrypt the uploaded files using the AWS Key Management Service \(AWS KMS\), choose **AWS KMS master\-key**\. Then choose a customer master key \(CMK\) from the list of AWS KMS CMKs\.
**Note**  
To encrypt objects in a bucket, you can use only CMKs that are available in the same AWS Region as the bucket\. 

         You can give an external account the ability to use an object that is protected by an AWS KMS CMK\. To do this, select **Custom KMS ARN** from the list and enter the Amazon Resource Name \(ARN\) for the external account\. Administrators of an external account that have usage permissions to an object protected by your AWS KMS CMK can further restrict access by creating a resource\-level IAM policy\. 

         For more information about creating an AWS KMS CMK, see [Creating Keys](https://docs.aws.amazon.com/kms/latest/developerguide/UsingServerSideEncryption.html) in the *AWS Key Management Service Developer Guide*\. For more information about protecting data with AWS KMS, see [Protecting Data Using Keys Stored in AWS KMS \(SSE\-KMS\)](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingServerSideEncryption.html) in the *Amazon Simple Storage Service Developer Guide*\.

   1. Metadata for Amazon S3 objects is represented by a name\-value \(key\-value\) pair\. There are two kinds of metadata: system\-defined metadata and user\-defined metadata\.

      If you want to add Amazon S3 system\-defined metadata to all of the objects you are uploading, for **Header**, select a header\. You can select common HTTP headers, such as **Content\-Type** and **Content\-Disposition**\. Type a value for the header, and then choose **Save**\. For a list of system\-defined metadata and information about whether you can add the value, see [System\-Defined Metadata](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html#SysMetadata) in the *Amazon Simple Storage Service Developer Guide*\.

   1. Any metadata starting with prefix `x-amz-meta-` is treated as user\-defined metadata\. User\-defined metadata is stored with the object, and is returned when you download the object\. 

      To add user\-defined metadata to all of the objects that you are uploading, type `x-amz-meta-` plus a custom metadata name in the **Header** field\. Type a value for the header, and then choose **Save**\. Both the keys and their values must conform to US\-ASCII standards\. User\-defined metadata can be as large as 2 KB\. For more information about user\-defined metadata, see [User\-Defined Metadata](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html#UserMetadata) in the *Amazon Simple Storage Service Developer Guide*\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/upload-set-properties-metadata.png)

   1. Object tagging gives you a way to categorize storage\. Each tag is a key\-value pair\. Key and tag values are case sensitive\. You can have up to 10 tags per object\. 

      To add tags to all of the objects that you are uploading, type a tag name in the **Key** field\. Type a value for the tag, and then choose **Save**\. A tag key can be up to 128 Unicode characters in length and tag values can be up to 255 Unicode characters in length\. For more information about object tags, see [Object Tagging](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html) in the *Amazon Simple Storage Service Developer Guide*\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/upload-set-object-tags.png)

1. Choose **Next**\.

1. On the **Upload** review page, verify that your settings are correct, and then choose **Upload**\. To make changes, choose **Previous**\.

1. To see the progress of the upload, choose **In progress** at the bottom of the browser window\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/operation-bar.png)  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/upload-object-progress-bar.png)

   To see a history of your uploads and other operations, choose **Success**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/operation-bar-success.png)

## Uploading Files by Pointing and Clicking<a name="upload-objects-by-file-selection"></a>

This procedure explains how to upload files into an S3 bucket by choosing **Upload**\.

**To upload files to an S3 bucket by pointing and clicking**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Bucket name** list, choose the name of the bucket that you want to upload your files to\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-bucket-name.png)

1. Choose **Upload**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/choose-upload.png)

1. In the **Upload** dialog box, choose **Add files**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/upload-add-files.png)

1. Choose one or more files to upload, and then choose **Open\.**   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/upload-select-files.png)

1. After you see the files that you chose listed in the **Upload** dialog box, do one of the following: 

   1. To add more files, choose **Add more files**\.

   1. To immediately upload the listed files, choose **Upload**\. 

   1. To set permissions or properties for the files that you are uploading, choose **Next**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/images/upload-display-file.png)

1. To set permissions and properties, start with **Step 5** of [Uploading Files and Folders by Using Drag and Drop](#upload-objects-by-drag-and-drop)\.

## More Info<a name="upload-objects-moreinfo"></a>
+ [How do I set permissions on an object?](set-object-permissions.md)\.
+  [How do I download an object from an S3 bucket?](download-objects.md)