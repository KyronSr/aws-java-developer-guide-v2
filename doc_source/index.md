# AWS SDK for Java Developer Guide

-----
## Contents
+ [Developer guide - AWS SDK for Java 2.x](home.md)
+ [Get started with the AWS SDK for Java 2.x](get-started.md)
+ [Setting up the AWS SDK for Java 2.x](setup.md)
   + [Setting up an Apache Maven project](setup-project-maven.md)
   + [Setting up a Gradle project](setup-project-gradle.md)
   + [Setting up a GraalVM Native Image project for the AWS SDK for Java](setup-project-graalvm.md)
   + [Additional setup information](setup-additional.md)
   + [Migrating from version 1.x to 2.x of the AWS SDK for Java](migration.md)
      + [What's different between the AWS SDK for Java 1.x and 2.x](migration-whats-different.md)
         + [Additional client changes](migration-client-changes.md)
         + [Credentials provider changes](migration-client-credentials.md)
         + [Region class name changes](migration-client-region.md)
         + [Exception class name changes](migration-exception-changes.md)
      + [Using the SDK for Java 1.x and 2.x side-by-side](migration-side-by-side.md)
+ [Using the AWS SDK for Java 2.x](using.md)
   + [Using credentials](credentials.md)
      + [Configuring IAM roles for Amazon EC2](ec2-iam-roles.md)
   + [AWS region selection](region-selection.md)
   + [Optimizing cold start performance for AWS Lambda](lambda-optimize-starttime.md)
   + [HTTP configuration](http-configuration.md)
      + [Configuring the AWS CRT-based HTTP client](http-configuration-crt.md)
      + [Configuring the Netty-based HTTP client](http-configuration-netty.md)
   + [Exception handling for the AWS SDK for Java](handling-exceptions.md)
   + [Logging AWS SDK for Java calls](logging-slf4j.md)
   + [Setting the JVM TTL for DNS name lookups](jvm-ttl-dns.md)
+ [Features of the AWS SDK for Java 2.x](features.md)
   + [Asynchronous programming](asynchronous.md)
   + [Using the DynamoDB Enhanced Client in the AWS SDK for Java 2.x](dynamodb-enhanced-client.md)
   + [Working with HTTP/2 in the AWS SDK for Java](http2.md)
   + [Enabling SDK metrics for the AWS SDK for Java](metrics.md)
      + [Service client metrics](metrics-list.md)
   + [Retrieving paginated results using the AWS SDK for Java 2.x](pagination.md)
   + [Amazon S3 Transfer Manager (Preview)](transfer-manager.md)
   + [Using waiters in the AWS SDK for Java 2.x](waiters.md)
+ [Code examples for the AWS SDK for Java 2.x](examples.md)
   + [Guided code examples for the AWS SDK for Java 2.x](examples-guided.md)
      + [Working with Amazon S3](examples-s3.md)
         + [Creating, listing, and deleting Amazon S3 buckets](examples-s3-buckets.md)
         + [Working with Amazon S3 objects](examples-s3-objects.md)
         + [Working with Amazon S3 presigned URLs](examples-s3-presign.md)
         + [Working with S3 Glacier](examples-glacier.md)
      + [Working with DynamoDB](examples-dynamodb.md)
         + [Working with tables in DynamoDB](examples-dynamodb-tables.md)
         + [Working with items in DynamoDB](examples-dynamodb-items.md)
         + [Mapping items in DynamoDB tables](examples-dynamodb-enhanced.md)
      + [Working with Amazon EC2](examples-ec2.md)
         + [Manage Amazon EC2 instances](examples-ec2-instances.md)
         + [Use elastic IP addresses in Amazon EC2](examples-ec2-elastic-ip.md)
         + [Use regions and availability zones](examples-ec2-regions-zones.md)
         + [Work with Amazon EC2 key pairs](examples-ec2-key-pairs.md)
         + [Work with security groups in Amazon EC2](examples-ec2-security-groups.md)
      + [Working with IAM](examples-iam.md)
         + [Managing IAM access keys](examples-iam-access-keys.md)
         + [Managing IAM Users](examples-iam-users.md)
         + [Using IAM account aliases](examples-iam-account-aliases.md)
         + [Working with IAM policies](examples-iam-policies.md)
         + [Working with IAM server certificates](examples-iam-server-certificates.md)
      + [Working with Amazon Athena](examples-athena.md)
      + [Working with CloudWatch](examples-cloudwatch.md)
         + [Getting metrics from CloudWatch](examples-cloudwatch-get-metrics.md)
         + [Publishing custom metric data to CloudWatch](examples-cloudwatch-publish-custom-metrics.md)
         + [Working with CloudWatch alarms](examples-cloudwatch-create-alarms.md)
         + [Using alarm actions in CloudWatch](examples-cloudwatch-use-alarm-actions.md)
         + [Sending events to CloudWatch](examples-cloudwatch-send-events.md)
      + [Working with AWS CloudTrail](examples-cloudtrail.md)
      + [Working with Amazon Cognito](examples-cognito.md)
      + [Working with Amazon Comprehend](examples-comprehend.md)
      + [Working with Amazon EventBridge](examples-eventbridge.md)
      + [Working with Amazon Kinesis Data Firehose](examples-firehose.md)
      + [Working with Amazon Forecast](examples-forecast.md)
      + [Working with AWS Glue](examples-glue.md)
      + [Working with Kinesis](examples-kinesis.md)
         + [Subscribing to Amazon Kinesis Data Streams](examples-kinesis-stream.md)
      + [Working with AWS Key Management Service](examples-kms.md)
      + [Invoke, list, and delete AWS Lambda functions](examples-lambda.md)
      + [Working with AWS Elemental MediaConvert](examples-mediaconvert.md)
      + [Working with AWS Elemental MediaStore](examples-mediastore.md)
      + [Working with AWS Migration Hub](examples-migrationhub.md)
      + [Working with Amazon Personalize](examples-personalize.md)
      + [Working with Amazon Pinpoint](examples-pinpoint.md)
      + [Working with Amazon Polly](examples-polly.md)
      + [Working with Amazon RDS](examples-rds.md)
      + [Working with Amazon Redshift](examples-redshift.md)
      + [Working with Amazon Rekognition](examples-rekognition.md)
      + [Working with Amazon SageMaker](examples-sagemaker.md)
      + [Working with AWS Secrets Manager](examples-secretsmanager.md)
      + [Working with Amazon Simple Email Service](examples-ses.md)
      + [Working with Amazon Simple Notification Service](examples-simple-notification-service.md)
      + [Working with Amazon Simple Queue Service](examples-sqs.md)
         + [Working with Amazon Simple Queue Service message queues](examples-sqs-message-queues.md)
         + [Sending, receiving, and deleting Amazon Simple Queue Service messages](examples-sqs-messages.md)
      + [Working with AWS Systems Manager](examples-ssm.md)
      + [Working with Amazon Simple Workflow Service](examples-swf.md)
      + [Working with Amazon Textract](examples-textract.md)
      + [Working with Amazon Transcribe](examples-transcribe.md)
         + [Working with Amazon Transcribe](examples-transcribe-bidirectional-streaming.md)
      + [Working with Amazon Translate](examples-translate.md)
      + [Working with Amazon WorkDocs](examples-workdocs.md)
   + [SDK for Java 2.x code examples](java_code_examples.md)
      + [Single-service actions and scenarios using SDK for Java 2.x](java_code_examples_categorized.md)
         + [API Gateway examples using SDK for Java 2.x](java_api-gateway_code_examples.md)
         + [Application Recovery Controller examples using SDK for Java 2.x](java_route53-recovery-cluster_code_examples.md)
         + [CloudFront examples using SDK for Java 2.x](java_cloudfront_code_examples.md)
         + [CloudWatch examples using SDK for Java 2.x](java_cloudwatch_code_examples.md)
         + [CloudWatch Events examples using SDK for Java 2.x](java_cloudwatch-events_code_examples.md)
         + [CloudWatch Logs examples using SDK for Java 2.x](java_cloudwatch-logs_code_examples.md)
         + [Amazon Cognito Identity Provider examples using SDK for Java 2.x](java_cognito-identity-provider_code_examples.md)
         + [Amazon Comprehend examples using SDK for Java 2.x](java_comprehend_code_examples.md)
         + [DynamoDB examples using SDK for Java 2.x](java_dynamodb_code_examples.md)
         + [Amazon EC2 examples using SDK for Java 2.x](java_ec2_code_examples.md)
         + [Amazon EC2 Auto Scaling examples using SDK for Java 2.x](java_auto-scaling_code_examples.md)
         + [EventBridge examples using SDK for Java 2.x](java_eventbridge_code_examples.md)
         + [AWS Glue examples using SDK for Java 2.x](java_glue_code_examples.md)
         + [IAM examples using SDK for Java 2.x](java_iam_code_examples.md)
         + [AWS KMS examples using SDK for Java 2.x](java_kms_code_examples.md)
         + [Kinesis examples using SDK for Java 2.x](java_kinesis_code_examples.md)
         + [Lambda examples using SDK for Java 2.x](java_lambda_code_examples.md)
         + [Amazon Personalize examples using SDK for Java 2.x](java_personalize_code_examples.md)
         + [Amazon Personalize Events examples using SDK for Java 2.x](java_personalize-events_code_examples.md)
         + [Amazon Personalize Runtime examples using SDK for Java 2.x](java_personalize-runtime_code_examples.md)
         + [Amazon Pinpoint examples using SDK for Java 2.x](java_pinpoint_code_examples.md)
         + [Amazon RDS examples using SDK for Java 2.x](java_rds_code_examples.md)
         + [Amazon Rekognition examples using SDK for Java 2.x](java_rekognition_code_examples.md)
         + [Amazon S3 examples using SDK for Java 2.x](java_s3_code_examples.md)
         + [S3 Glacier examples using SDK for Java 2.x](java_glacier_code_examples.md)
         + [Amazon SES examples using SDK for Java 2.x](java_ses_code_examples.md)
         + [Amazon SNS examples using SDK for Java 2.x](java_sns_code_examples.md)
         + [Amazon SQS examples using SDK for Java 2.x](java_sqs_code_examples.md)
         + [Secrets Manager examples using SDK for Java 2.x](java_secrets-manager_code_examples.md)
         + [Amazon Textract examples using SDK for Java 2.x](java_textract_code_examples.md)
      + [Cross-service examples using SDK for Java 2.x](java_code_examples_cross_service.md)
         + [Build an application to submit data to a DynamoDB table](cross_SubmitDataApp_java_topic.md)
         + [Create an Amazon Lex Chatbot within a web application to engage your web site visitors](cross_LexChatbotLanguages_java_topic.md)
         + [Build a publish and subscription application that translates messages](cross_SnsPublishSubscription_java_topic.md)
         + [Create a dynamic web application to track DynamoDB data](cross_DynamoDBDataTracker_java_topic.md)
         + [Create an Amazon Relational Database Service item tracker](cross_RDSDataTracker_java_topic.md)
         + [Detect PPE in images with Amazon Rekognition using an AWS SDK](cross_RekognitionPhotoAnalyzerPPE_java_topic.md)
         + [Detect objects in images with Amazon Rekognition using an AWS SDK](cross_RekognitionPhotoAnalyzer_java_topic.md)
         + [Detect people and objects in a video with Amazon Rekognition using an AWS SDK](cross_RekognitionVideoDetection_java_topic.md)
         + [Use API Gateway to invoke a Lambda function](cross_LambdaAPIGateway_java_topic.md)
         + [Use Step Functions to invoke Lambda functions](cross_ServerlessWorkflows_java_topic.md)
         + [Use scheduled events to invoke a Lambda function](cross_LambdaScheduledEvents_java_topic.md)
+ [Security for the AWS SDK for Java](security.md)
   + [Data protection in AWS SDK for Java 2.x](security-data-protection.md)
   + [AWS SDK for Java support for TLS](security-java-tls.md)
   + [Identity and Access Management for this AWS Product or Service](security-iam.md)
   + [Compliance validation for the AWS SDK for Java](security-compliance-validation.md)
   + [Resilience for this AWS Product or Service](security-resilience.md)
   + [Infrastructure Security for this AWS Product or Service](security-infrastructure.md)
+ [Document history](document-history.md)