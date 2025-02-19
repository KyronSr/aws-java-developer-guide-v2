--------

You can now use the [Amazon S3 Transfer Manager \(Developer Preview\)](https://bit.ly/2WQebiP) in the AWS SDK for Java 2\.x for accelerated file transfers\. Give it a try and [let us know what you think](https://bit.ly/3zT1YYM)\! By the way, the AWS SDK for Java team is hiring [software development engineers](https://github.com/aws/aws-sdk-java-v2/issues/3156)\!

--------

# Creating, listing, and deleting Amazon S3 buckets<a name="examples-s3-buckets"></a>

Every object \(file\) in Amazon S3 must reside within a *bucket*\. A bucket represents a collection \(container\) of objects\. Each bucket must have a unique *key* \(name\)\. For detailed information about buckets and their configuration, see [Working with Amazon S3 Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev/UsingBucket.html) in the Amazon Simple Storage Service User Guide\.

**Note**  
Best Practice  
We recommend that you enable the [AbortIncompleteMultipartUpload](http://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTlifecycle.html) lifecycle rule on your Amazon S3 buckets\.  
This rule directs Amazon S3 to abort multipart uploads that don’t complete within a specified number of days after being initiated\. When the set time limit is exceeded, Amazon S3 aborts the upload and then deletes the incomplete upload data\.  
For more information, see [Lifecycle Configuration for a Bucket with Versioning](http://docs.aws.amazon.com/AmazonS3/latest/user-guide/lifecycle-configuration-bucket-with-versioning.html) in the Amazon Simple Storage Service User Guide\.

**Note**  
These code snippets assume that you understand the material in basics, and have configured default AWS credentials using the information in [Set default credentials and Region](setup.md#setup-credentials)\.

**Topics**
+ [Create a bucket](#create-bucket)
+ [List the buckets](#list-buckets)
+ [Delete a bucket](#delete-bucket)

## Create a bucket<a name="create-bucket"></a>

Build a [CreateBucketRequest](http://docs.aws.amazon.com/sdk-for-java/latest/reference/software/amazon/awssdk/services/s3/model/CreateBucketRequest.html) and provide a bucket name\. Pass it to the S3Client’s `createBucket` method\. Use the `S3Client` to do additional operations such as listing or deleting buckets as shown in later examples\.

 **Imports** 

```
import software.amazon.awssdk.core.waiters.WaiterResponse;
import software.amazon.awssdk.regions.Region;
import software.amazon.awssdk.services.s3.S3Client;
import software.amazon.awssdk.services.s3.model.*;
import software.amazon.awssdk.services.s3.waiters.S3Waiter;
```

 **Code** 

First create an S3Client\.

```
        Region region = Region.US_WEST_2;
        S3Client s3 = S3Client.builder()
                .region(region)
                .build();
```

Make a Create Bucket Request\.

```
    // Create a bucket by using a S3Waiter object
    public static void createBucket( S3Client s3Client, String bucketName) {

        try {
            S3Waiter s3Waiter = s3Client.waiter();
             CreateBucketRequest bucketRequest = CreateBucketRequest.builder()
                    .bucket(bucketName)
                    .build();

            s3Client.createBucket(bucketRequest);
            HeadBucketRequest bucketRequestWait = HeadBucketRequest.builder()
                    .bucket(bucketName)
                    .build();


            // Wait until the bucket is created and print out the response
            WaiterResponse<HeadBucketResponse> waiterResponse = s3Waiter.waitUntilBucketExists(bucketRequestWait);
            waiterResponse.matched().response().ifPresent(System.out::println);
            System.out.println(bucketName +" is ready");

        } catch (S3Exception e) {
            System.err.println(e.awsErrorDetails().errorMessage());
            System.exit(1);
        }
    }
```

See the [complete example](https://github.com/awsdocs/aws-doc-sdk-examples/blob/master/javav2/example_code/s3/src/main/java/com/example/s3/S3BucketOps.java) on GitHub\.

## List the buckets<a name="list-buckets"></a>

Build a [ListBucketsRequest](http://docs.aws.amazon.com/sdk-for-java/latest/reference/software/amazon/awssdk/services/s3/model/ListBucketsRequest.html)\. Use the S3Client’s `listBuckets` method to retrieve the list of buckets\. If the request succeeds a [ListBucketsResponse](http://docs.aws.amazon.com/sdk-for-java/latest/reference/software/amazon/awssdk/services/s3/model/ListBucketsResponse.html) is returned\. Use this response object to retrieve the list of buckets\.

 **Imports** 

```
import software.amazon.awssdk.core.waiters.WaiterResponse;
import software.amazon.awssdk.regions.Region;
import software.amazon.awssdk.services.s3.S3Client;
import software.amazon.awssdk.services.s3.model.*;
import software.amazon.awssdk.services.s3.waiters.S3Waiter;
```

 **Code** 

First create an S3Client\.

```
        Region region = Region.US_WEST_2;
        S3Client s3 = S3Client.builder()
                .region(region)
                .build();
```

Make a List Buckets Request\.

```
        // List buckets
        ListBucketsRequest listBucketsRequest = ListBucketsRequest.builder().build();
        ListBucketsResponse listBucketsResponse = s3.listBuckets(listBucketsRequest);
        listBucketsResponse.buckets().stream().forEach(x -> System.out.println(x.name()));
```

See the [complete example](https://github.com/awsdocs/aws-doc-sdk-examples/blob/master/javav2/example_code/s3/src/main/java/com/example/s3/S3BucketOps.java) on GitHub\.

## Delete a bucket<a name="delete-bucket"></a>

Before you can delete an Amazon S3 bucket, you must ensure that the bucket is empty or the service will return an error\. If you have a [versioned bucket](http://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html), you must also delete any versioned objects that are in the bucket\.

**Topics**
+ [Delete objects in a bucket](#delete-objects-in-a-bucket)
+ [Delete an empty bucket](#delete-an-empty-bucket)

### Delete objects in a bucket<a name="delete-objects-in-a-bucket"></a>

Build a [ListObjectsV2Request](http://docs.aws.amazon.com/sdk-for-java/latest/reference/software/amazon/awssdk/services/s3/model/ListObjectsV2Request.html) and use the S3Client’s `listObjects` method to retrieve the list of objects in the bucket\. Then use the `deleteObject` method on each object to delete it\.

 **Imports** 

```
import software.amazon.awssdk.core.waiters.WaiterResponse;
import software.amazon.awssdk.regions.Region;
import software.amazon.awssdk.services.s3.S3Client;
import software.amazon.awssdk.services.s3.model.*;
import software.amazon.awssdk.services.s3.waiters.S3Waiter;
```

 **Code** 

First create an S3Client\.

```
        Region region = Region.US_WEST_2;
        S3Client s3 = S3Client.builder()
                .region(region)
                .build();
```

Delete all objects in the bucket\.

```
        DeleteBucketRequest deleteBucketRequest = DeleteBucketRequest.builder().bucket(bucket).build();
        s3.deleteBucket(deleteBucketRequest);
        s3.close();
```

See the [complete example](https://github.com/awsdocs/aws-doc-sdk-examples/blob/master/javav2/example_code/s3/src/main/java/com/example/s3/S3BucketDeletion.java) on GitHub\.

### Delete an empty bucket<a name="delete-an-empty-bucket"></a>

Build a [DeleteBucketRequest](http://docs.aws.amazon.com/sdk-for-java/latest/reference/software/amazon/awssdk/services/s3/model/DeleteBucketRequest.html) with a bucket name and pass it to the S3Client’s `deleteBucket` method\.

 **Imports** 

```
import software.amazon.awssdk.core.waiters.WaiterResponse;
import software.amazon.awssdk.regions.Region;
import software.amazon.awssdk.services.s3.S3Client;
import software.amazon.awssdk.services.s3.model.*;
import software.amazon.awssdk.services.s3.waiters.S3Waiter;
```

 **Code** 

First create an S3Client\.

```
        Region region = Region.US_WEST_2;
        S3Client s3 = S3Client.builder()
                .region(region)
                .build();
```

Delete all objects in the bucket\.

```
    public static void deleteBucketObjects(S3Client s3, String bucketName, String objectName) {

        ArrayList<ObjectIdentifier> toDelete = new ArrayList<ObjectIdentifier>();
        toDelete.add(ObjectIdentifier.builder().key(objectName).build());

        try {
            DeleteObjectsRequest dor = DeleteObjectsRequest.builder()
                    .bucket(bucketName)
                    .delete(Delete.builder().objects(toDelete).build())
                    .build();
            s3.deleteObjects(dor);
        } catch (S3Exception e) {
            System.err.println(e.awsErrorDetails().errorMessage());
            System.exit(1);
        }
        System.out.println("Done!");
    }
```

Delete the bucket\.

```
        DeleteBucketRequest deleteBucketRequest = DeleteBucketRequest.builder().bucket(bucket).build();
        s3.deleteBucket(deleteBucketRequest);
        s3.close();
```

See the [complete example](https://github.com/awsdocs/aws-doc-sdk-examples/blob/master/javav2/example_code/s3/src/main/java/com/example/s3/S3BucketOps.java) on GitHub\.