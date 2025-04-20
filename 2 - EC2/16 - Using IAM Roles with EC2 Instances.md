# Using IAM Roles with EC2 Instances

- **IAM Roles** provide secure AWS credentials to EC2 instances
- Preferred method over manual credential configuration
- Enables temporary, rotating credentials for enhanced security

### Key Concepts
- **Never store IAM credentials** directly on EC2 instances
- Roles provide temporary permissions through:
  - Automatic credential rotation
  - No manual key management
  - Fine-grained access control

### How to Attach an IAM Role
1. **Connect to your EC2 instance** using:
   - EC2 Instance Connect (browser-based)
   - Traditional SSH client
2. **Navigate to EC2 console**:
   - Select your instance
   - Go to **Actions → Security → Modify IAM Role**
3. **Choose existing role** (e.g., `DemoRoleForEC2`)
4. **Save changes** to attach the role

### Practical Demonstration
1. **Without IAM Role**:
```bash
aws iam list-users
# Returns "Unable to locate credentials"
```

2. **After attaching role**:
```bash
aws iam list-users
# Successfully returns IAM user list
```

3. **Role removal**:
```bash
aws iam list-users
# Returns "Access Denied" after detaching role
```

### Best Practices
- **Always use IAM roles** instead of:
  - Hardcoding credentials
  - Running `aws configure` on instances
- **Policy attachment**:
  - Attach minimal required permissions
  - Changes may take a few minutes to propagate
- **Monitoring**:
  - Use CloudTrail to track role usage
  - Implement permission boundaries

### Troubleshooting
- If commands fail after role attachment:
  1. Verify role is properly assigned
  2. Check IAM policy permissions
  3. Allow time for changes to propagate (1-2 minutes)
  4. Ensure instance has internet access for STS calls

### Security Benefits
- Eliminates credential leakage risks
- Automatic credential rotation
- No need to manually revoke credentials
- Centralized permission management

