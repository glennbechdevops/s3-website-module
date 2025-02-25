# S3 Static Website Terraform Configuration

This Terraform configuration sets up an S3 bucket configured for static website hosting with public read access.

## Important Note on Public Access Block Settings

The configuration includes a deliberate 10-second delay between applying the public access block settings and the bucket policy. This delay is necessary because AWS S3 public access block changes can take several seconds to propagate fully through AWS's systems.

Without this delay, you might encounter the following error:

Error: error putting S3 policy: AccessControlListNotSupported: The bucket policy cannot be set on a bucket that has public access block settings enabled


The delay is implemented using the `time_sleep` resource, which ensures that the public access block settings are fully propagated before the bucket policy is applied.

## Resources Created

- S3 Bucket
- Bucket Policy (public read access)
- Website Configuration
- Public Access Block Settings (disabled to allow public access)

## Usage

Simply apply the Terraform configuration:

bash
terraform init
terraform apply


The website will be accessible at the S3 bucket website endpoint after the configuration is applied.