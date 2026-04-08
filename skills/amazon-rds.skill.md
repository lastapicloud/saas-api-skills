---
name: amazon-rds
description: Manage RDS database instances via AWS API. Use when the user mentions
  rds, amazon rds, aws rds, database instance, aurora.
version: 1.0.0
skill_type: external
base_url_env: AMAZON_RDS_BASE_URL
auth_env_var: AMAZON_RDS_BASE_URL
auth_type: header
triggers:
  - rds
  - amazon rds
  - aws rds
  - database instance
  - aurora
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires AMAZON_RDS_BASE_URL and AMAZON_RDS_BASE_URL environment variables.
---

# Amazon-Rds

Manage RDS database instances via AWS API. Use when the user mentions rds, amazon rds, aws rds, database instance, aurora.

## API Endpoints

- **GET** `/?Action=DescribeDBInstances` - List DB instances
- **GET** `/?Action=DescribeDBClusters` - List DB clusters
- **POST** `/?Action=CreateDBInstance` - Create a DB instance
- **POST** `/?Action=DeleteDBInstance` - Delete a DB instance
- **POST** `/?Action=ModifyDBInstance` - Modify a DB instance
- **POST** `/?Action=RebootDBInstance` - Reboot a DB instance
- **GET** `/?Action=DescribeDBSnapshots` - List DB snapshots
- **POST** `/?Action=CreateDBSnapshot` - Create a DB snapshot
- **GET** `/attribute-groups` - Lists all attribute groups which you have access to. Results are paginated.
- **POST** `/attribute-groups` - Creates a new attribute group as a container for user-defined attributes. This feature enables users to have full
- **PATCH** `/attribute-groups/{attributeGroup}` - Updates an existing attribute group with new details.
- **DELETE** `/attribute-groups/{attributeGroup}` - Deletes an attribute group, specified either by its attribute group ID, name, or ARN.
- **GET** `/applications` - Retrieves a list of all of your applications. Results are paginated.
- **POST** `/applications` - Creates a new application that is the top-level node in a hierarchy of related cloud resource abstractions.
- **PATCH** `/applications/{application}` - Updates an existing application with new attributes.

## Actions

- list: List DB instances (GET /?Action=DescribeDBInstances)
- list_actiondescribedbclusters: List DB clusters (GET /?Action=DescribeDBClusters)
- create: Create a DB instance (POST /?Action=CreateDBInstance)
- create_actiondeletedbinstance: Delete a DB instance (POST /?Action=DeleteDBInstance)
- create_actionmodifydbinstance: Modify a DB instance (POST /?Action=ModifyDBInstance)
- create_actionrebootdbinstance: Reboot a DB instance (POST /?Action=RebootDBInstance)
- list_actiondescribedbsnapshots: List DB snapshots (GET /?Action=DescribeDBSnapshots)
- create_actioncreatedbsnapshot: Create a DB snapshot (POST /?Action=CreateDBSnapshot)
- list_attribute_groups: Lists all attribute groups which you have access to. Results are paginated. (GET /attribute-groups)
- create_attribute_groups: Creates a new attribute group as a container for user-defined attributes. This f (POST /attribute-groups)
- update: Updates an existing attribute group with new details. (PATCH /attribute-groups/{attributeGroup})
- delete: Deletes an attribute group, specified either by its attribute group ID, name, or (DELETE /attribute-groups/{attributeGroup})
- list_applications: Retrieves a list of all of your applications. Results are paginated. (GET /applications)
- create_applications: Creates a new application that is the top-level node in a hierarchy of related c (POST /applications)
- update_applications: Updates an existing application with new attributes. (PATCH /applications/{application})

## Fields

- `DBInstanceIdentifier`: string [REQUIRED]
- `DBInstanceClass`: string [REQUIRED for create]
- `Engine`: string [REQUIRED for create]
- `MasterUsername`: string [REQUIRED for create]

## Example Request Bodies

**Create DB Instance:**
```json
{"DBInstanceIdentifier": "mydb-instance", "DBInstanceClass": "db.t3.medium", "Engine": "mysql", "MasterUsername": "admin"}
```

**Modify DB Instance:**
```json
{"DBInstanceIdentifier": "mydb-instance", "DBInstanceClass": "db.t3.large"}
