# EC2 Instance Connect


- **EC2 Instance Connect** provides a browser-based SSH session to EC2 instances
- Alternative to traditional SSH clients (Terminal, PuTTY, etc.)
- No need to manage SSH keys manually

### How to Connect
1. Select your EC2 instance in AWS Console
2. Click **Connect** button at the top
3. Choose **EC2 Instance Connect** option
4. Default username (e.g., `ec2-user` for Amazon Linux) is auto-filled
5. Click **Connect** to establish session

### Key Features
- Automatically uploads temporary SSH key
- No SSH key management required
- Direct browser-based terminal access
- Supports all standard Linux commands (`whoami`, `ping`, etc.)

### Requirements
- Security group must allow **port 22 (SSH)** access:
  - From your IP address (recommended) or
  - From anywhere (`0.0.0.0/0` for IPv4, `::/0` for IPv6)
  
### Troubleshooting
- If connection fails:
  1. Verify security group has SSH (port 22) inbound rule
  2. Check both IPv4 and IPv6 rules if needed
  3. Ensure correct username for your AMI type

### Advantages Over Traditional SSH
- No need for:
  - SSH client installation
  - Key pair management
  - Manual key file permissions setup
- Quick access directly from AWS Console
- Temporary credentials enhance security

### Limitations
- Still uses SSH protocol behind the scenes
- Requires port 22 access (same as traditional SSH)
- Browser-based session may have fewer features than full terminal

### Best Practices
- Maintain proper security group rules
- Use temporary sessions for quick access
- For production environments, consider combining with:
  - IAM permissions for EC2 Instance Connect
  - Session logging

---

**Next Steps**: Continue to use EC2 Instance Connect for hands-on exercises in the course.