# EC2 and EBS Volume Management


## Viewing Existing Volumes
- Access the **Storage** tab in the EC2 instance dashboard to see attached EBS volumes.


## Navigating to EBS Volume Console
- Clicking on the volume opens the **EBS Volumes Console**.
- This interface shows volume state (e.g., “in use”) and associated instances.

## Creating and Attaching Additional Volumes
- You can create new EBS volumes (e.g., a 2 GB GP2 volume).
- Volumes must be created in the **same Availability Zone (AZ)** as the EC2 instance to be attached.
- After creation, use the **“Attach Volume”** action to link it to an EC2 instance.
- Once attached, the instance will reflect multiple block devices in its storage tab.

## Availability Zone Binding
- EBS volumes are **AZ-specific**. A volume created in a different AZ (e.g., `eu-west-1a` vs `eu-west-1b`) cannot be attached to an instance outside its AZ.

## Volume Lifecycle Management
- EBS volumes can be easily **deleted** from the console.
- This shows the **flexibility and power of cloud infrastructure**.

## Volume Persistence on Termination
- Root volumes have a **“Delete on Termination”** attribute (default is `true`).
- This can be modified during instance creation under **advanced storage settings**.
- Upon EC2 instance termination, root volumes with this flag set to `true` are automatically deleted.
- Other attached volumes without this flag persist and remain available.

