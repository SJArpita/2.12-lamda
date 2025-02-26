1.What is the purpose of the execution role on the Lambda function?
Ans. The execution role in AWS Lambda is an IAM role that grants the Lambda function permissions to interact with other AWS services. It defines what actions the function can perform on AWS resources.
2.What is the purpose of the resource-based policy on the Lambda function?
Ans. A resource-based policy on an AWS Lambda function controls who (users, roles, AWS services, or accounts) can invoke the function. Unlike execution roles, which define what the function itself can do, resource-based policies define who can invoke or manage the function.
3.If the function is needed to upload a file into an S3 bucket, describe (i.e no need for the actual policies)
What is the needed update on the execution role?
What is the new resource-based policy that needs to be added (if any)?
Ans.If a Lambda function needs to upload a file into an S3 bucket, two key permission updates are required:
A:Update to the Execution Role (Lambda's IAM Role)
Since the execution role defines what the Lambda function can do, it must be updated to allow:
Writing files to the S3 bucket
Listing or getting objects (if needed)
The execution role should be updated to grant write permissions (s3:PutObject) on the target S3 bucket.
B:Resource-Based Policy on the S3 Bucket (if needed)
A resource-based policy is only required if:
The Lambda function is in a different AWS account than the S3 bucket.
The bucket needs to allow public access or access from another AWS service (not recommended).
In this case, an S3 bucket policy must be added to allow the Lambda function's IAM role to perform actions like s3:PutObject on the specific bucket.
