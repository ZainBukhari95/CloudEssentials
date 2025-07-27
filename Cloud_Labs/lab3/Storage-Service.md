# Storage Service

This Project shows three fundamental storage services on HUAWEI CLOUD: Elastic Volume Service (EVS), Object Storage Service (OBS), and Scalable File Service (SFS). The lab exercises are designed to give users practical experience in provisioning, managing, and utilizing these services to meet various business needs.

Elastic Volume Service (EVS) Practice
The first part of the lab focuses on EVS, which provides persistent block-level storage for Elastic Cloud Servers (ECSs). EVS disks function similarly to physical hard drives and are used to expand storage capacity for servers. The exercise demonstrates the entire lifecycle of an EVS disk.

The process begins with setting up the network environment by creating a Virtual Private Cloud (VPC) and a subnet. Then, a Windows ECS is provisioned. Following this, a separate EVS data disk is purchased. A key concept highlighted is that EVS disks must be in the same Availability Zone (AZ) as the ECS to which they will be attached.

Once the EVS disk is in an "Available" state, it is manually attached to the Windows ECS. The guide then details the crucial step of disk initialization. After attaching a new disk, a user must log in to the Windows Server, use the "Disk Management" utility to bring the disk online, initialize it (choosing between MBR and GPT partition styles), and then create and format a new simple volume. This makes the disk appear as a new drive (e.g., D:) in "This PC."

To demonstrate data persistence and disk portability, a test file is created on the newly mounted EVS volume. The disk is then properly taken offline within the Windows OS before being detached from the first ECS via the HUAWEI CLOUD console. A second Windows ECS is purchased, and the same EVS disk is attached to it. After logging into the new ECS and bringing the disk online, the exercise verifies that the previously created test file is still present, confirming that data on an EVS disk is persistent and independent of any single ECS instance.

The lab repeats a similar process for a Linux environment. A Linux ECS is created, and an EVS disk is attached. The guide provides a detailed walkthrough of the command-line procedures for initializing the disk in Linux. This involves using the fdisk utility to create a new partition on the disk (/dev/vdb), followed by the mkfs command to format the new partition with a file system like ext4. A mount point (a directory) is created, and the mount command is used to attach the file system to that directory. The exercise also covers how to configure automatic mounting at system startup by editing the /etc/fstab file, ensuring the disk is available after a reboot.

Finally, the EVS section introduces the use of snapshots. A snapshot captures the state of an EVS disk at a specific point in time. The lab shows how to create a snapshot of the Linux data disk, and then create a brand new EVS disk from that snapshot. This new disk, when attached to an ECS, contains an exact copy of the data from the original disk at the time the snapshot was taken, demonstrating a powerful method for data backup, recovery, and cloning.
Object Storage Service (OBS) Practice

The second section shifts focus to OBS, HUAWEI CLOUD's service for storing massive amounts of unstructured data, such as documents, images, and videos. Unlike the block storage of EVS, OBS is an object storage system. The exercise covers the basic operations within OBS.
The fundamental unit in OBS is the "bucket," a container for data. The lab guides the user through creating a bucket, specifying its region, storage class (e.g., Standard), and access policy (e.g., Private). Once the bucket is created, the user learns how to upload files from their local computer into the bucket. The process for downloading objects from the bucket back to a local machine is also shown, as is the procedure for deleting files and folders within the bucket. This section provides a foundational understanding of how to use the OBS console for basic data management tasks.

Scalable File Service (SFS) Practice
The final part of the document covers SFS, which provides high-performance, shared file storage. SFS is ideal for use cases where multiple servers need to access and modify the same set of files simultaneously.
The exercise demonstrates how to create an "SFS Turbo" file system within the previously established VPC. After the file system is created, the main task is to mount it on both a Linux and a Windows ECS.

For the Linux ECS, the lab requires installing the NFS client (nfs-utils). It then shows how to use the mount command with the NFS protocol to connect the SFS file system's unique mount address to a local directory on the ECS. A test file is created in this shared directory.
For the Windows ECS, the "Client for NFS" feature must be installed through the "Server Manager." After a reboot, the mount command is used in the Command Prompt to map the SFS file system to a drive letter. When the user navigates to this new drive, they can see the test file created from the Linux ECS, successfully demonstrating that SFS allows seamless, shared file access across servers running different operating systems.

(![IMG-20250727-WA0033](https://github.com/user-attachments/assets/5d9a7a10-58bf-4164-bbcb-614da257d673)
![IMG-20250727-WA0032](https://github.com/user-attachments/assets/660306bd-fd9c-4c25-8c18-a4fa14c281f4)
![IMG-20250727-WA0031](https://github.com/user-attachments/assets/1c38c665-c1e4-4ea1-b9a9-fcc9ba6bbcbd)
![IMG-20250727-WA0030](https://github.com/user-attachments/assets/2d30028a-e569-4b96-9ca9-295b541eee31)
![WhatsApp Image 2025-07-27 at 20 52 22_c6cf7fdb](https://github.com/user-attachments/assets/81f8005c-5153-4b39-ad31-0c84b515022b)
![IMG-20250727-WA0037](https://github.com/user-attachments/assets/59e5ce78-d15d-4b34-90a8-a2e561ab708e)
![IMG-20250727-WA0036](https://github.com/user-attachments/assets/0a160373-fe3c-4627-9f60-959942bda6c4)
![IMG-20250727-WA0035](https://github.com/user-attachments/assets/5ca7ec7f-2617-4b81-a8b6-34e10b9d18a9)
![IMG-20250727-WA0034](https://github.com/user-attachments/assets/d1c2216a-6d58-4d36-acce-e8e576dc117a)
)
