- IAM manages access to AWS resources
- Who is authenticated and what they are authorized to do
- Three types of identities
    - users
    - groups
    - roles
- IAM policies define what resources user/group/role have access to and what actions they can perform on the resources.
- Create user → assign policies. CANNOT directly assign permissions.

## policy example

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:ListBucket"
      ],
      "Resource": [
        "arn:aws:s3:::example-bucket",
        "arn:aws:s3:::example-bucket/*"
      ]
    }
  ]
}
```

- **Version**: Specifies the policy language version. Always use `"2012-10-17"` unless you have a specific reason to use an older version.
- **Statement**: Contains one or more permission statements.
    - **Effect**: `"Allow"` grants permission, while `"Deny"` explicitly denies it.
    - **Action**: Lists the actions allowed (e.g., `s3:GetObject` for reading objects and `s3:ListBucket` for listing bucket contents).
    - **Resource**: Specifies the AWS resources the actions apply to. In this case, the bucket (`arn:aws:s3:::example-bucket`) and its contents (`arn:aws:s3:::example-bucket/*`).

### **How `Deny` Works in IAM**

IAM evaluates policies using the following rules:

1. **Explicit Deny**: If any policy explicitly denies an action, it is denied, regardless of any `Allow` permissions.
2. **Explicit Allow**: If no `Deny` exists and at least one policy allows the action, it is permitted.
3. **Implicit Deny**: If no policy explicitly allows or denies the action, it is implicitly denied.

This is often summarized as: **`Deny` > `Allow` > `Implicit Deny`**.

## Users

An IAM user is an entity that represents a person or an application that interacts with AWS services. While IAM users are often associated with human users, they are equally well-suited for representing applications, services, or automated processes.

## Groups

Attach policies to groups then assign users to groups. Consider the following

- group IT, assign a set of appropriate policies
- group Marketing, assign another set of appropriate policies

After creating a new user, one can just assign the user to a group.

## Roles

1. **Roles are temporary**: When a user assumes a role, they temporarily gain the permissions associated with that role.
2. **Role policies replace user policies**:
    - When a user assumes a role, their **original permissions (user policies)** are temporarily **replaced** by the permissions of the role.

## Summary (SCP is applied in organization)
Service Control Policy (SCP)

1️⃣ **SCPs define the maximum permissions an AWS account can have.**
- IAM policies determine what actions a user or role can actually perform **within the SCP limits**.

2️⃣ **Evaluation Order of Permissions:**
1. **Explicit Deny** (in SCP or IAM) → 🚫 **Always wins.**
2. **Explicit Allow** (in SCP or IAM) → ✅ Only applies **if there’s no explicit deny**.
3. **Implicit Deny** (default state) → ⛔ Applies when there's no explicit allow.

💡 **Key Clarification:**
- SCPs **do not grant permissions**—they only limit what IAM policies can do.
- An **Allow in an SCP does nothing unless an IAM policy also allows it.**
- An **Explicit Deny in SCP or IAM always blocks the action, even if another policy allows it.**