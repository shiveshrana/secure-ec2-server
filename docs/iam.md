# IAM Configuration

## IAM Group

### Group Name

`EC2-Developers`

### Attached Policy

`AmazonEC2FullAccess`

The group provides permissions required to manage EC2 resources for this learning project.

## IAM Design

Permissions are assigned through an IAM group rather than directly attaching policies to the user.

```text
ec2-admin
    │
    ▼
EC2-Developers
    │
    ▼
AmazonEC2FullAccess

