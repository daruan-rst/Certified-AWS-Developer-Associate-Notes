# EBS vs EFS 

### Elastic Block Storage

- EBS Volumes:
    - Are attached to on instance at a time (except multi-attatch io1/io2) 
    - are locked at the Availability Zone (AZ) level
    - gp2: IO increases if the disk size increases
    - gp3 & io1: can increase IO independently

- To migrate an EBS volume across AZ
    - Take a snapshot
    - Restore the snapshot to another AZ
    - EBS backups use IO and you shouldn’t run
    them while your application is handling a lot
    of traffic

- Root EBS Volumes of instances get
terminated by default if the EC2 instance
gets terminated. (you can disable that)

<br><br>

![EBS-Snapshot-example](/3%20-%20EBS/images/4-EBS-Snapshot.svg)

<br><br>

### Elastic File System
- Mounting 100s of instances across AZ
- EFS share website files (WordPress)
- Only for Linux Instances (POSIX)
- EFS has a higher price point than EBS
- Can leverage Storage Tiers for cost savings


<br><br>
![EFS](/3%20-%20EBS/images/5-EFS.svg)
