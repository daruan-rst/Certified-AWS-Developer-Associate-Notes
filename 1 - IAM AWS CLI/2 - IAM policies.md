# IAM Policies

- IAM policies are the permissions a user or a group of users have.
- If a policy is attached to a group, than every member of said group wiil inherit its policy
- If a user belongs to multiple groups, than it will inherit the policies of every group it belongs to
If a user does not belong to a group, it is still possible to create a inline policy only attached to it

- Example:

![IAM Groups Example](/1%20-%20IAM%20AWS%20CLI/images/2-IAMPoliciesExample.drawio.svg)

**Figure 1:** This diagram illustrates how policies are inherited in IAM groups in AWS. 

- IAM policy structure consists of:
- **Version:** policy language version, always include "2012-10-17"
- **Id:** An identifier for the policy (optional)
- **Statement:** one or more individual statements (required)
- Statements consist of:
    - **Sid:** an identifier for the statement (optional)
    - **Effect:** whether the statement allows or denies access (Allow, Deny)
    - **Principal:** account / user / role to which this policy applied to
    - **Action:** List of actions a policy allows or denies
    - **Resource:** List of resources to which this actions applied to
    - **Condition:** conditions for when the policy is in effect (optional)  

- Example of policies JSON:

 ```
  {
  "Version": "2012-10-17",
  "Id"
  "Statement": [
    {
      "Sid": "FirstStatement",
      "Effect": "Allow",
      "Action": ["iam:ChangePassword"],
      "Resource": "*"
    },
    {
      "Sid": "SecondStatement",
      "Effect": "Allow",
      "Action": "s3:ListAllMyBuckets",
      "Resource": "*"
    },
    {
      "Sid": "ThirdStatement",
      "Effect": "Allow",
      "Action": [
        "s3:List*",
        "s3:Get*"
      ],
      "Resource": [
        "arn:aws:s3:::amzn-s3-demo-bucket-confidential-data",
        "arn:aws:s3:::amzn-s3-demo-bucket-confidential-data/*"
      ],
      "Condition": {"Bool": {"aws:MultiFactorAuthPresent": "true"}}
    }
  ]
}
```