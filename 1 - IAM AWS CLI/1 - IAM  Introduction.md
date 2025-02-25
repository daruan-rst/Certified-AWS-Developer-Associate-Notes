# IAM
- IAM = Identity and access management
- IAM is a Global Service
- A root account is created by default abd shouldn't be used or shared
- Used to create users and assign them to a group
- Users are people within your organization and they can be grouped
- Groups can only contain users and not other groups
- Users can belong to multiple groups (and may also belong to no group at all)

- Example:


### Permissions
 - We create users and groups in order to allow them to use the AWS account based on permissions named __policies__
  - Users or groups can be assigned JSON documents called policies
  - In AWS we apply the least priviledge principle: don't give more permission than a user needs.