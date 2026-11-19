---
name: aws-s3-storage
description: "Manage buckets and objects in Amazon S3. Use when the user mentions s3, aws, bucket, object, storage, upload, download, file."
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
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
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
- **PUT** `/{Bucket}` - <p>Creates a new S3 bucket. To create a bucket, you must register with Amazon S3 and have a valid Amazon Web Services
- **GET** `/{Bucket}` - <p>Returns some or all (up to 1,000) of the objects in a bucket. You can use the request parameters as selection

## Actions

- list: List all buckets (GET /)
- update: Create a bucket (PUT /{bucket})
- delete: Delete a bucket (DELETE /{bucket})
- get_by_id: List objects in a bucket (GET /{bucket})
- head_resource: Get bucket metadata (HEAD /{bucket})
- update_resource: Upload an object (PUT /{bucket}/{key})
- get_by_id_resource: Download an object (GET /{bucket}/{key})
- delete_resource: Delete an object (DELETE /{bucket}/{key})
- head_resource_8: Get object metadata (HEAD /{bucket}/{key})
- create_resource: Delete multiple objects (batch delete) (POST /{bucket})
- list_resource: List multipart uploads (GET /{bucket}?uploads)
- create: Upload part (multipart) (POST /{bucket}/{key}?partNumber)
- create_resource_2: Complete multipart upload (POST /{bucket}/{key}?uploadId)
- create_bucket: <p>Creates a new S3 bucket. To create a bucket, you must register with Amazon S3 (PUT /{Bucket})
- list_objects: <p>Returns some or all (up to 1,000) of the objects in a bucket. You can use the (GET /{Bucket})

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

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request — missing required field, wrong type, or constraint violation |
| 401 | Authentication failed — check API credentials |
| 403 | Forbidden — insufficient permissions |
| 404 | Resource not found |
| 429 | Rate limited — retry after delay |
| 500 | Server error |
