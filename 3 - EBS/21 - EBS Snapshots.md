# EBS Snapshots
 - Make a backup (snapshot) of your EBS volume at a point in time
 - Not necessary to detach volume to do snapshot, but recommended
 -  Can copy snapshots across AZ or Region

 ### Features
#### EBS Snapshot Archive
- Move a Snapshot to an "archive tier" that is 75% cheaper
- Takes within 24 to 72 hours for restoring the archive
<br>

#### Recycle Bin for EBS Snapshot 
- Setup rules to retain deleted snapshots so you can recovern them after an accidental deletion
- Specify retention (from 1 day to year 1)
<br>

#### First Snapshot Restore
- Force full initialization of snapshot to have no latency on the first use
