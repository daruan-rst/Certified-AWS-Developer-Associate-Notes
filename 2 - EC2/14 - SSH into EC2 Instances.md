# SSH into EC2 Instances

|                  | **SSH** | **Putty** | **EC2 Instance Connect** |
|------------------|:-------:|:---------:|:------------------------:|
| **MAC**          |    X    |           |             X            |
| **LINUX**        |    X    |           |             X            |
| **Windows < 10** |         |     X     |             X            |
| **Windows > 10** |    X    |     X     |             X            |



## Introduction to SSH
- **SSH (Secure Shell)** is a crucial tool for remotely accessing and managing servers, especially in cloud environments like AWS.
- It allows you to control a remote machine using the command line.
- SSH is essential for performing maintenance or actions on your EC2 instances.

---

## SSH Methods Based on Operating Systems

### SSH on Linux & Mac


#### Connecting to a Remote Server
To connect to an EC2 instance:
```
ssh -i /path/to/your/key.pem user@your-server-ip
```
- `-i`: Specifies the private key file.
- `user`: Typically `ec2-user` for Amazon Linux, `ubuntu` for Ubuntu.
- `your-server-ip`: The public IP address of your instance.

#### Configuring SSH Keys
1. Generate a key pair if you don't have one:
   ```
   ssh-keygen -t rsa -b 4096 -f ~/.ssh/my-key
   ```
2. Upload the public key to the remote server:
   ```
   ssh-copy-id user@your-server-ip
   ```

### SSH on Windows (Pre-Windows 10)
#### Using PuTTY
For older Windows versions, PuTTY is a commonly used SSH client.
1. Download and install PuTTY.
2. Open PuTTY and enter the server IP.
3. Under "Connection -> SSH -> Auth," load your private key (`.ppk` format).
4. Click "Open" to initiate the connection.

#### Converting PEM to PPK
If using AWS, private keys are usually in `.pem` format. Convert it to `.ppk` using PuTTYgen:
1. Open PuTTYgen.
2. Load your `.pem` file.
3. Click "Save private key" to generate a `.ppk` file.

### SSH on Windows 10 and Later
Windows 10 includes a built-in OpenSSH client.
#### Connecting via Command Prompt or PowerShell
Use the same SSH command as on Linux/Mac:
```
ssh -i C:\path\to\your\key.pem user@your-server-ip
```

### Alternative: EC2 Instance Connect
EC2 Instance Connect allows browser-based SSH access without requiring terminal commands. It works across all operating systems but is currently limited to Amazon Linux 2 instances.

### Troubleshooting SSH Issues
- Check security group rules to allow SSH (port 22).
- Verify the private key file permissions (Linux/Mac: `chmod 400 key.pem`).
- Ensure the username matches the instance type.
- Use EC2 Instance Connect as a fallback option.



