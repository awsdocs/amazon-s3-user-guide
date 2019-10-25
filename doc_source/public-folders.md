# Making Folders Public<a name="public-folders"></a>

Amazon S3 has a flat structure instead of a hierarchy like you would typically see in a file system\. However, for the sake of organizational simplicity, the Amazon S3 console supports a folder concept as a way to group objects\. In Amazon S3, the folder is a naming prefix for an object or group of objects\. For more information, see [How Do I Use Folders in an S3 Bucket?](using-folders.md)

We recommend blocking all public access to your Amazon S3 folders and buckets unless you specifically require a public folder or bucket\. When you make a folder public, anyone on the internet can view all the objects that are grouped in that folder\. In the Amazon S3 console, you can make a folder public\. You can also make a folder public by creating a bucket policy that limits access by prefix\. For more information, see [Setting Bucket and Object Access Permissions](set-permissions.md)\. 

**Warning**  
After you make a folder public in the Amazon S3 console, you can't make it private again\. Instead, you must set permissions on each individual object in the public folder so that the objects have no public access\. For more information, see [How Do I Set Permissions on an Object?](set-object-permissions.md)

## More Info<a name="public-folders-moreinfo"></a>
+ [How Do I Delete Folders from an S3 Bucket?](delete-folders.md)
+ [How Do I Set ACL Bucket Permissions?](set-bucket-permissions.md)
+ [How Do I Block Public Access to S3 Buckets?](block-public-access.md)