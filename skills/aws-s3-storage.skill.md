---
name: aws-s3-storage
description: Manage buckets and objects in Amazon S3. Use when the user mentions s3,
  aws, bucket, object, storage, upload, download, file.
version: 1.0.0
skill_type: external
base_url_env: AWS_S3_BASE_URL
auth_env_var: AWS_S3_BASE_URL
auth_type: header
triggers:
  - s3
  - aws
  - bucket
  - object
  - storage
  - upload
  - download
  - file
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires AWS_S3_BASE_URL and AWS_S3_BASE_URL environment variables.
---

# Aws-S3-Storage

Manage buckets and objects in Amazon S3. Use when the user mentions s3, aws, bucket, object, storage, upload, download, file.

## API Endpoints

- **GET** `/` - List all buckets
- **PUT** `/{bucket}` - Create a bucket
- **DELETE** `/{bucket}` - Delete a bucket
- **GET** `/{bucket}` - List objects in a bucket
- **HEAD** `/{bucket}` - Get bucket metadata
- **PUT** `/{bucket}/{key}` - Upload an object
- **GET** `/{bucket}/{key}` - Download an object
- **DELETE** `/{bucket}/{key}` - Delete an object
- **HEAD** `/{bucket}/{key}` - Get object metadata
- **POST** `/{bucket}` - Delete multiple objects (batch delete)
- **GET** `/{bucket}?uploads` - List multipart uploads
- **POST** `/{bucket}/{key}?partNumber` - Upload part (multipart)
- **POST** `/{bucket}/{key}?uploadId` - Complete multipart upload

## Actions

- list: List all buckets (GET /)
- create: Create a bucket (PUT /{bucket})
- delete: Delete a bucket (DELETE /{bucket})
- list_objects: List objects in a bucket (GET /{bucket})
- head_bucket: Get bucket metadata (HEAD /{bucket})
- upload: Upload an object (PUT /{bucket}/{key})
- download: Download an object (GET /{bucket}/{key})
- delete_object: Delete an object (DELETE /{bucket}/{key})
- head_object: Get object metadata (HEAD /{bucket}/{key})
- delete_multiple: Delete multiple objects (POST /{bucket})
- list_uploads: List multipart uploads (GET /{bucket}?uploads)
- upload_part: Upload part (POST /{bucket}/{key}?partNumber)
- complete_upload: Complete multipart upload (POST /{bucket}/{key}?uploadId)

## Fields

- `bucket`: string [REQUIRED for bucket/object actions] (bucket name)
- `key`: string [REQUIRED for object actions] (object key/path)
- `prefix`: string [OPTIONAL for list_objects] (filter by key prefix)
- `max-keys`: integer [OPTIONAL for list_objects] (max results, default 1000)
- `Content-Type`: string [OPTIONAL for upload_object] (MIME type of the object)
- `x-amz-acl`: string [OPTIONAL for upload_object] (canned ACL: private, public-read)

## Example Request Bodies

**List Objects (Query Params):**
Query parameter: `list-type=2&prefix=photos/&max-keys=100`

**Create Bucket:**
```xml
<CreateBucketConfiguration><LocationConstraint>us-east-1</LocationConstraint></CreateBucketConfiguration>
```

**Upload Object:**
Binary body with `Content-Type` header set to the file's MIME type.
