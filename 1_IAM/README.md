# IAM

## What is it?

- AWS IAM (Identity and Access Management) is a service that enables you to securely manage access to AWS resources.
- IAM is a global service and is essential for controlling who can access what in your AWS environment.
- With IAM, you can create users, groups, and roles, and control their permissions using policies. 
- IAM helps you follow the principle of least privilege, ensuring that each identity only has the minimum permissions needed to perform its tasks.


## Important Components

### Users

- IAM Users represent individual people or services that need access to AWS.
- Each user has credentials (username, password, access keys).
- Users can be granted permissions directly or through group membership.

### Groups

- Groups are collections of IAM users.
- Policies attached to a group apply to all its members.
- Useful for managing permissions for a team or department (e.g., Developers, Admins).
- IAM User Group can contain only IAM users (can't contain user group!!)

### Roles
- Roles are temporary identities that AWS services or users can assume.
- Unlike IAM users (which have long-term credentials), IAM roles don’t have credentials; instead, they’re assumed with secure tokens.

- Why Use Roles → Secure Access for AWS Services
  - Example: An EC2 instance needs to access an S3 bucket.
      - Instead of storing access keys on the instance (which is unsafe), you assign a role to the instance.
      - EC2 temporarily assumes the role and gets permission to access S3.

- Commonly used for:
  - Granting EC2 instances access to S3
  - Lambda Function Roles
  - Roles for CloudFormation

### Policies

- Policies are JSON documents that define permissions (Allow or Deny).
- Policies specify:
  - Actions (e.g., `s3:PutObject`)
  - Resources (e.g., a specific S3 bucket)
  - conditions (Optional)
- Policies can be attached to users, groups, or roles.

### Security Features

- MFA (Multi-Factor Authentication)
  - Adds an extra layer of login security.
- Password Policies
  - Customize strong password rules.
- Credential Reports
  - Account Level, show the status of users' passwords, access keys, and MFA.
- IAM Last Accessed
  - User Level, helps identify unused permissions or risky access.

## Security best practices in IAM
#### The following bullet points are summarized from the official [AWS IAM best practices guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#bp-users-federation-idp).
- Require human users to use federation with an identity provider to access AWS using temporary credentials
- Require workloads to use temporary credentials with IAM roles to access AWS
- Require multi-factor authentication (MFA)
- Update access keys when needed for use cases that require long-term credentials
- Follow best practices to protect your root user credentials
- Apply least-privilege permissions
- Get started with AWS managed policies and move toward least-privilege permissions
- Use IAM Access Analyzer to generate least-privilege policies based on access activity
- Regularly review and remove unused users, roles, permissions, policies, and credentials
- Use conditions in IAM policies to further restrict access
- Verify public and cross-account access to resources with IAM Access Analyzer
- Use IAM Access Analyzer to validate your IAM policies to ensure secure and functional permissions
- Establish permissions guardrails across multiple accounts
- Use permissions boundaries to delegate permissions management within an account