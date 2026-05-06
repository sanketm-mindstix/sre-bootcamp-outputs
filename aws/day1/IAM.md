## IAM 
IAM (Identity and Access Management) is the framework used by AWS in cloud computing to manage and control 
- who (Users, Application, Services) can access 
- what (Application, Resources, Services) and
- under what conditions (permissions, policies, authentications)

#### 3 Rules of IAM
1. **Implicit deny** — if no policy explicitly allows an action, it is denied. There is no "default allow" anywhere in AWS. A brand new IAM user can do nothing.
2. **Explicit allow** — a policy must explicitly grant the action on the specific resource.
3. **Explicit deny** — if any policy explicitly denies an action, it is denied regardless of any allows. Explicit deny always wins.


### Users and Groups
Root Account is created by default , shoudn't be used or shared

**Users** are people within your org and can be grouped
Note - Users don't have to belong to any group, and user can belong to multiple groups

**Groups** only contain users, not other groups
 

### IAM:Permissions
Users and Groups can be assigned policies (JSON Doc) which specifies permissions
This policies defines the permissions for users.

Example -
```bash
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:ListBucket"],
      "Resource": ["arn:aws:s3:::my-app-bucket"]
    },
    {
      "Effect": "Allow",
      "Action": ["s3:GetObject", "s3:PutObject"],
      "Resource": ["arn:aws:s3:::my-app-bucket/*"]
    }
  ]
}
```
#### Identity based policies VS Resource based policies
Identity based policies can be attached to the Users, Groups or Roles. This help let us specify what that identity can do

Resource based policies can be attached to the resources like S3 Buckets, VPC Endpoints, SQS Queues

### IAM:Roles
An IAM Role is a set of permissions (policies) that doesn’t belong to a specific user, but can be assumed temporarily.

No username/password
Used by:
- AWS services (EC2, Lambda)
- IAM users
- External accounts (cross-account access)

### Assume Role (What does it mean?)
Assume Role = temporarily getting access to a role

You get temporary credentials (Access Key, Secret, Session Token)
These expire (usually minutes to hours)

### IAM:Trust Policy 
A Trust Policy defines WHO is allowed to assume the role

Example-
```bash
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::123456789012:user/sanket"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```
Only that specific user can assume the role.

#### Permission Policy vs Trust Policy
| Type                  | Purpose                         |
| --------------------- | ------------------------------- |
| **Trust Policy**      | Who can assume the role         |
| **Permission Policy** | What they can do after assuming |

#### Very useful in the following scenario
User from Account A wants access to Account B
Role-A in Account B trusts Account A
User in A assumes role in B
