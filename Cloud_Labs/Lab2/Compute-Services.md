# Compute Services

Deploying HUAWEI CLOUD's Elastic Cloud Server (ECS) and Image Management Service (IMS). It walks users through creating, managing, customizing, and capturing server configurations to streamline future deployments.
ECS Creation and Basic Management
The lab begins by establishing a foundational network environment by creating a Virtual Private Cloud (VPC). This provides an isolated virtual network for the servers.
Once the VPC is ready, the guide details the process of provisioning two distinct types of servers:
1.	A Windows ECS, using a "Windows Server 2012 R2" public image.
2.	A Linux ECS, using a "CentOS 7.6" public image.
For both, the user configures basic settings like pay-per-use billing, region (AP-Singapore), instance size (CPU and memory), and system disk type. The Windows ECS is initially created without a public Elastic IP (EIP), while the Linux ECS is configured to auto-assign one. The user sets a password for login during the creation process.
After creation, the lab explains how to log in to the servers. For the Windows ECS, this is done via the console's "Remote Login" feature, which uses a VNC client. For the Linux ECS, which has a command-line interface only, the user also uses the VNC-based "Remote Login" to access the terminal, entering root as the username and the previously set password.
The guide also covers how to modify the specifications of an existing ECS. To change resources like memory, the server must first be stopped. Once stopped, the "Modify Specifications" option becomes available, allowing the user to select new hardware configurations. After the modification is submitted, the ECS is restarted to apply the changes.
Creating and Using Private Images
A core part of the lab focuses on the Image Management Service (IMS), which allows users to create custom private images from configured ECSs. This is a powerful feature for creating a "golden master" server template with all necessary software and settings pre-installed, enabling rapid deployment of identical servers.
Windows Image Creation
Before creating an image from the Windows ECS, several configuration steps are necessary to ensure that new servers created from the image will function correctly:
•	Networking: Verify the network interface card (NIC) is set to obtain IP and DNS addresses automatically (DHCP).
•	Remote Access: Enable "Remote Desktop" connections and configure Windows Firewall to allow the necessary traffic.
•	Initialization Tool: Check that Cloudbase-Init is installed. This crucial tool, installed by default on public images, handles the injection of custom information (like passwords and hostnames) into new ECSs created from the image.
With the ECS configured, the user navigates to the IMS console and creates a new "System disk image," selecting the prepared Windows ECS as the source.
Linux Image Creation
The process for Linux is similar, requiring specific pre-configuration checks:
•	Networking: Ensure DHCP is enabled in the network configuration files.
•	Initialization Tools: Verify that both Cloud-Init (the Linux equivalent of Cloudbase-Init) and the one-click password reset plug-in are installed. These are typically present on public images.
•	Network Rules: Delete any persistent network rule files (/etc/udev/rules.d) to prevent network interface naming conflicts on new ECSs created from the image.
After these checks, a private image is created from the Linux ECS in the same way as the Windows one.
Managing and Sharing Images
Once private images are created, the lab demonstrates further management capabilities. Users can modify image information, such as the name and description. They can also replicate an image within the same region to create a copy for backup or use in a different project.
Finally, the guide explains how to share a private image with another HUAWEI CLOUD account. This is useful for collaboration or providing standardized server templates to other users. The process involves obtaining the Project ID of the recipient's account, using the "Share" function on the private image, and adding the recipient's Project ID. The recipient must then log in to their account and formally accept the shared image to be able to use it. The lab concludes by showing how to launch a new ECS directly from a created private image, completing the workflow from server configuration to streamlined deployment.

(![IMG-20250727-WA0050](https://github.com/user-attachments/assets/78f9c9bc-383c-4acb-9169-b793323dff33)
![IMG-20250727-WA0049](https://github.com/user-attachments/assets/b3c78143-b520-47e3-a5df-32c2f93d8cf8)
![IMG-20250727-WA0048](https://github.com/user-attachments/assets/0884a416-49e1-4bfa-8f5f-a6833975b057)
![IMG-20250727-WA0047](https://github.com/user-attachments/assets/b76f0bc0-f36d-42bb-9e25-ff71a39b5cb1)
![IMG-20250727-WA0046](https://github.com/user-attachments/assets/75ad0bfe-5d20-4f68-8ee7-3df08c4f1f93)
![IMG-20250727-WA0045](https://github.com/user-attachments/assets/64c152a3-7274-4786-9160-050b0154f3d5)
![IMG-20250727-WA0044](https://github.com/user-attachments/assets/66723f5f-5ae4-48f2-853f-0414b4d35201)
![IMG-20250727-WA0043](https://github.com/user-attachments/assets/5566dc9d-9918-4578-a395-0e67b49703fe)
![IMG-20250727-WA0042](https://github.com/user-attachments/assets/1dda1e47-d197-4018-98af-9851fab29ac5)
![IMG-20250727-WA0041](https://github.com/user-attachments/assets/b9c0f2a1-6fba-469b-95fb-6996f3edc77a)
![IMG-20250727-WA0040](https://github.com/user-attachments/assets/e5a2a054-3bff-46b4-9129-9182fff115f4)
![IMG-20250727-WA0039](https://github.com/user-attachments/assets/accc5101-6833-41f9-8365-23011d564465)
![IMG-20250727-WA0052](https://github.com/user-attachments/assets/b3205a78-ad28-4fde-8ffa-ff228058dcc4)
![IMG-20250727-WA0051](https://github.com/user-attachments/assets/9b7c44a0-5491-441d-be2d-fe1e9d2d2215)
)

