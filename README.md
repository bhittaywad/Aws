 # Repo to learn Aws with practice. Contributions are most welcome.
 # # AWS Learning Guide

This repository serves as a guide for learning Infra designing,cost optimization,fault tolerant,scalabillity and security  

## Table of Contents

Introduction to AWS
- 1-EC2
  
  
  
          |-----------------|-----------------|-----------------|
          |     AMI         |      SG         |     ENI         |
          |     Template    |      On-demand   |Reseved Instance|
          |Schedule instance| Spot Instance   |Dedicated Instanc|
          |capacity reserve | Saving plan     |placement group  |
          |Ec2 troubleshot  |networking seting|Moniter and trobl|
          |Ec2 status check |

- 2-EBS STORAGE
- 3-VPC
- 4-Load-balancer
- 5-Auto-scalling
- 6-Route53
- 7-S3 bucket
- 8-IAM User
- 9-RDS
- 10-Terraform
- 11-ECS

# Ami
before Ami

1- ec2 instance don't backup

after Ami

1- ec2 instance backup

# Ec2 troubleshuting 
1- Attach with auto-scalling
2- change protection termination
3 - change stop & start protection 
4 - change shutdown behavior
5 - change auto-recovery behavior

# Ec2 Networking setting

1 - Attach network interface 

## why we need interface card

1 - more than workload and  NIC attach to ec2 instance

2- It works like a load balancer 

2 - Connect RDS database

3 - change source /destination

4 - Diassociate elastic Ip


# How to check status

1 - system status check

2 - instance status check 

## system status check 
if this check fail,there might issue with infrastructure that is hosting such as Aws power,Networking software system

## Instance status check 
Ec2 instance to identify hardware/software issue
Reboot
terminate
launch replacement

# Aws instance type
## General purpose: 
Normal purpose  (testing)
## Compute optimize:
High CPU
## Memory optimize
High memory
## Accerlated computing
High graphic
## Storage optimize
High storage 

# On-Demand
No capacity

High price 

Per hour payment

# Reserved instance 

Capacity guranty

Low price 

## payment plan:

1-No-upfront

2-Partial upfront

3-All upfront

1-3 year reserved

No, cancellation 

# Schedule instance 

capacity guranty

schdule instance available no every region

everyday  a running a instance 9:00am to 10:00pm


# Capacity reservation instance

On-demand ,capacity guranty reserved

# saving plan

On-demand price discount


# Dedicated Host

Complete rack buy 

High cost

Storage manage

Capacity gurantee

No, security issue

# spot instance

As a bids

90% discount 


# Placement group

The main idea is to control how and where instances are placed within a data center or across multiple data centers to achieve specific goals, such as improving performance, reducing latency, or enhancing fault tolerance.

## Cluster Placement Group: 
Instances are placed close to each other within a single Availability Zone. This setup is ideal for applications that require low network latency or high network throughput, such as high-performance computing (HPC) applications.

1.# Cluster Placement Group
Purpose:To enhance network performance by placing instances in close physical proximity within the same Availability Zone.
## Benefits:
1-Low latency communication between instances.

2-High network throughput, beneficial for high-performance computing (HPC) and data-intensive applications.

## Spread Placement Group:
Instances are distributed across underlying hardware to reduce the risk of simultaneous failures. This is useful for applications that need to be highly available and resilient to hardware failures. It ensures that instances are spread across different hardware racks.
2. # Spread Placement Group
Purpose: To minimize the risk of simultaneous failures by spreading instances across multiple hardware units within an Availability Zone.
## Benefits:
1-High fault tolerance and availability, as instances are distributed across different racks and hardware.

2-Reduces the likelihood that a single point of failure will affect multiple instances.

## Partition Placement Group: 
Instances are divided into partitions, with each partition being isolated from others. This is beneficial for large distributed and replicated workloads where you want to avoid the risk of a single point of failure affecting all instances. Examples include big data applications and distributed databases.
3.# Partition Placement Group
Purpose: To group instances into partitions, with each partition isolated from others. This is useful for distributed applications where failure isolation is important.
## Benefits:
1-Enhanced fault tolerance as failures in one partition do not impact other partitions.

2-Can reduce the impact of hardware failures on large-scale applications by isolating them into different partitions.



# EBS VOLUME
## Elastic Block Store (EBS): 
In computing, especially in cloud services, EBS is a service provided by Amazon Web Services (AWS) that offers block storage volumes for use with Amazon EC2 instances. It provides high-performance storage that is both durable and scalable.

1- # Amazon Elastic Block Store (EBS):
## General Purpose SSD (gp2):
gp2: Suitable for a broad range of workloads. Performance scales with volume size, providing up to 10,000 IOPS and 250 MB/s of throughput


## Provisioned IOPS SSD (io2/io1): 

Designed for I/O-intensive applications requiring high performance and low latency.
## Throughput Optimized HDD (st1):

Suitable for large, sequential workloads, like big data and data warehousing.

## Cold HDD (sc1):
Best for infrequent access to data, like long-term storage.
## Snapshot:
 A point-in-time backup of your EBS volume, useful for disaster recovery and data migration.

 # EBS storage family:
 gp2:
 
 min= 1GB

 max= 16384GB
 
 IOPs= min= 100
 
  max= 16000
  

GP3:

min= 1GB

max= 16384GB

IOPS= min=3000

max= 16000

throughput= min=125MB

max=1000MB

IO1:

min= 4GB

max=16384GB

IOPS= min= 100

max= 25000

throughput= Not applicable

IO2:

min= 4GB

max= 65535GB

IOPS= min= 100

max= 256000

throughput= Not applicable

Multi attach ec2 

SC1:

min= 125GB

max= 1634GB

IOPS= Not

Throughput=min= 6MB

max= 250MB

ST1:

min= 125GB

max= 16384GB

IOPS= Not

throughput= min= 20MB

max= 500MB

# How to attach additional Ebs volume to an ec2 instance 

## 1. Create an EBS Volume

- Go to the AWS Management Console.
- 
## Navigate to the EC2 Dashboard:

- Select "EC2" from the Services menu.
## Open the EBS Volumes Page:

In the left-hand menu, under "Elastic Block Store", select "Volumes".

## Create a New Volume:

- Click the "Create volume" button.
- 
- Configure your volume with the required specifications (size, type, availability zone, etc.).
- 
- Ensure the availability zone of the volume matches the availability zone of your EC2 instance.
  
  2. # Attach the EBS Volume to Your EC2 Instance
     
  1-  ## Select the Volume:

In the EBS Volumes page, select the newly created volume.

2- ## Attach the Volume:

- Click the "Actions" button, then select "Attach volume".
- In the "Attach volume" dialog:
- Choose your EC2 instance from the "Instance" dropdown menu.
- Enter a "Device name" (e.g., /dev/sdf, /dev/sdg). The device name can vary depending on the operating system of your EC2 instance.
- Click "Attach".
 1- ## Connect to Your EC2 Instance:
  
 2- ## List Available Disks:
 
 lsblk
 3- ## Format the Volume:
 
 sudo mkfs -t ext4 /dev/xvdf
4- ## Create a Mount Point:

- Create a directory where the volume will be mounted:
- 
  sudo mkdir /mnt/myvolume

5- ## Mount the Volume:

- Mount the volume to the directory
- 
  sudo mount /dev/xvdf /mnt/myvolume
  
 6- ## Verify the Mount:

- Check the mounted file system
  
 df -h
7- ## Make the Mount Permanent (Optional):

- To ensure the volume mounts automatically after a reboot, add it to /etc/fstab. Open /etc/fstab with a text editor:
  
 vim /etc/fstab

4. # Unmounting and Detaching the Volume

  sudo umount /mnt/myvolume

 2- ## Detach the Volume:

- Go back to the EC2 Dashboard in the AWS Management Console.
- Select "Volumes" under "Elastic Block Store".
- Select the volume you want to detach.
- Click "Actions" and choose "Detach volume"
  3- ## Delete the Volume (Optional):

- If you no longer need the volume, you can delete it by selecting it and clicking "Actions" → "Delete volume".

  # How to root volume extend
  1- ## Stop the EC2 Instance (Optional)

- This step is optional, but it’s safer to stop the instance before making changes to the root volume. Go to the EC2 Dashboard, select your instance, and choose "Instance State" → "Stop".

 2- ## Modify the EBS Volume

- Open the AWS Management Console and go to the EC2 Dashboard.
- Select "Volumes" under "Elastic Block Store".
- Find your root volume (you can identify it by checking the volume ID associated with your instance).
- Select the volume and choose "Actions" → "Modify Volume".
- Increase the "Size" to your desired capacity and click "Modify". Confirm the modification when prompted.

  3- ## Start the EC2 Instance (if stopped)

- If you stopped your instance, go back to the "Instances" section and start it again
  
 4- ## Connect to Your EC2 Instance
 - lsblk

5- ## Resize the File System:

- For ext2/ext3/ext4 file systems, use
- sudo resize2fs /dev/xvda1
- For XFS file systems, use:
- growpart /dev/xvda 1
- xfs_growfs /dev/xvda1

  # How to reduce ebs volume
  -  ebs volume cannot reduce volume
    ## solution:
  Select the Volume you want to reduce in size.
  - attach ec2 instance
  - Choose the desired size, type, and ensure it's in the same availability zone as your old volume.
    # 2. Attach Both Volumes to the Temporary Instance

    1- Attach the Original Volume and the New Volume to the temporary EC2 instance:
- Go to the "Volumes" section in the EC2 Dashboard.
- Select each volume, click "Actions" → "Attach Volume", and attach them to the temporary instance.
  5.## Copy Data to the New Volume
1- ## Connect to the Temporary EC2 Instance using SSH or RDP.

2- ## Prepare the Volumes:

- List block devices to identify the attached volumes.
- Create a file system on the new volume if it doesn’t have one
- sudo mkfs -t ext4 /dev/xvdf
 3- ## Mount Both Volumes
  - Create mount points and mount the volumes
    sudo mkdir /mnt/oldvolume
    
sudo mkdir /mnt/newvolume

sudo mount /dev/xvda1 /mnt/oldvolume

sudo mount /dev/xvdf /mnt/newvolume
4- ## Copy Data:
- Use rsync or similar tools to copy the data from the old volume to the new one
- sudo rsync -aAXv /mnt/oldvolume/ /mnt/newvolume/
5- ## Unmount the Volumes after the data has been copied:
  - sudo umount /mnt/oldvolume
-sudo umount /mnt/newvolume

3. # Swap Volumes on Your Original Instance
  

1. Detach Both Volumes from the temporary instance.
2. 

3. Attach the New, Smaller Volume to your original EC2 instance as the root volume:

- Go to "Volumes", select the new volume, click "Actions" → "Attach Volume", and attach it to your instance.
- Update the device name to match the root device name of your instance (e.g., /dev/xvda).
- 
3. Detach the Old Volume:
  

- Detach the old volume from the instance

# How to attach ebs volume in different zone
  ### 1. Create a Snapshot of the Existing Volume

  ## Summary
- Create a Snapshot: Capture the data from the original EBS volume.
- Create a New Volume: Use the snapshot to create a new volume in the desired AZ.
- Attach the New Volume: Attach the new volume to your instance.
- 
By following these steps, you can effectively move and attach an EBS volume to an instance in a different availability zone. If you have further questions or run into any issues, feel free to ask!

# How to attach ebs volume in different region

## Steps to Attach an EBS Volume in a Different Region

## Summary

1. Create a Snapshot of the EBS volume in the source region.

2. Copy the Snapshot to the target region.

3. Create a New Volume in the target region from the copied snapshot.

4. Attach the New Volume to an EC2 instance in the target region.

By following these steps, you can successfully move and attach an EBS volume to an instance in a different AWS region. If you have any additional questions or run into issues, feel free to ask!






  
  


  


  

 


   



 















  



