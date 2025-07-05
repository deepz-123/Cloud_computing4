# Cloud_computing4
**COMPANY**    :  CODTECH IT SOLUTIONS
**NAME**       :  DEEPAK 
**INTERN ID**  :  CT04MRV
**DOMAIN**     :  CLOUD COMPUTING 
**DURATION**   :  4 MONTHS 
**MENTOR**     :  NEELA SANTOSH 
**DESCRIPTION**:

**Task: Implement IAM Policies, Secure Storage, and Data Encryption on AWS**

This task demonstrates how to secure cloud resources on Amazon Web Services (AWS) by implementing Identity and Access Management (IAM) policies, configuring secure storage, and applying data encryption techniques. Security is a critical component of any cloud infrastructure, and AWS provides a comprehensive set of tools and services to manage access, protect data, and ensure compliance.

The goal of this task is to follow best practices in securing AWS resources, specifically by defining precise IAM policies, securing storage services like S3, and ensuring that data is encrypted both at rest and in transit.
Tools & Services Used

Cloud Provider: Amazon Web Services (AWS)

Services:

AWS Identity and Access Management (IAM)

Amazon S3 (Simple Storage Service)

AWS Key Management Service (KMS)

AWS CloudTrail (optional for auditing)


Platform: AWS Management Console

Documentation: GitHub README.md

**Step-by-Step Implementation**

1. Create a Custom IAM Policy

Navigate to IAM > Policies

Click Create Policy, then choose the JSON tab

Define a custom policy (example: read-only access to a specific S3 bucket):


{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:GetObject"],
      "Resource": ["arn:aws:s3:::your-bucket-name/*"]
    }
  ]
}

Review and create the policy


2. Attach Policy to a User or Role

Go to IAM > Users or Roles

Select the user or role and click Add permissions

Attach the previously created policy


3. Secure Amazon S3 Bucket

Navigate to S3 > Your Bucket > Permissions

Block public access unless explicitly required

Set bucket policies and ACLs carefully

Enable versioning for recovery from accidental deletions


4. Enable Server-Side Encryption (SSE)

In your S3 bucket settings, go to Properties > Default Encryption

Choose:

SSE-S3: Server-side encryption with Amazon S3-managed keys

SSE-KMS: Server-side encryption with AWS Key Management Service


You may also create a Customer Managed Key (CMK) in KMS for more control


5. Ensure Data Encryption in Transit

By default, AWS S3 supports HTTPS

Make sure to access all S3 resources via HTTPS endpoints

Optionally enforce this in your bucket policy:


{
  "Sid": "AllowSSLRequestsOnly",
  "Effect": "Deny",
  "Principal": "*",
  "Action": "s3:*",
  "Resource": ["arn:aws:s3:::your-bucket-name/*"],
  "Condition": {
    "Bool": {
      "aws:SecureTransport": "false"
    }
  }
