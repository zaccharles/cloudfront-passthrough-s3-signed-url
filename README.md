# CloudFront Passthrough S3 Signed URL

1. Create a new CloudFormation stack using [cloudformation.template](cloudformation.template).
2. Upload [example-s3-object.json](example-s3-object.json) to the S3 bucket (link in "Resources" tab of CloudFormation stack).
3. Go to Lambda console for function (again, link in "Resources" tab of CloudFormation stack).
4. Invoke Lambda function with test event containing [lambda-test-event.json](lambda-test-event.json).
5. Output contains a S3 signed URL in `s3` and equivalent in `cf` property.
6. Use browser or something like Postman to GET the URL and check the response's `Content-Encoding` header.

Notes:
* CloudFront only compresses files with the `Content-Type` header values listed [here](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/ServingCompressedFiles.html#compressed-content-cloudfront-file-types).
* CloudFront only compresses files that are between 1,000 bytes and 10,000,000 bytes in size.
* See [Serving compressed files](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/ServingCompressedFiles.htm) for more.
