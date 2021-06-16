# CloudFront Passthrough S3 Signed URL

1. Create a new CloudFormation stack using [cloudformation.template](cloudformation.template).
2. Upload [example-s3-object.json](example-s3-object.json) to the S3 bucket (link in "Resources" tab of CloudFormation stack).
3. Go to Lambda console for function (again, link in "Resources" tab of CloudFormation stack).
4. Invoke Lambda function with test event containing [lambda-test-event.json](lambda-test-event.json).
5. Output contains a S3 signed URL in the `s3` and its CloudFront equivalent in the `cf` property.
6. Use a browser or something like Postman to GET the `cf` URL.
7. Confirm the response was compressed by checking the `Content-Encoding` header for `gzip` or `br`.

Notes:
* The S3 object can be accessed directly from the bucket using the `s3` URL.
* There is no way to determine the `s3` URL from the `cf` URL.
* CloudFront only compresses files with a `Content-Type` header value listed [here](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/ServingCompressedFiles.html#compressed-content-cloudfront-file-types).
* CloudFront only compresses files that are between 1,000 bytes and 10,000,000 bytes in size.
* Read [Serving compressed files](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/ServingCompressedFiles.html) for more information.
