# Deploying Enterprise on Web

Deploying a scalable and highly available enterprise website on HUAWEI CLOUD. The primary requirements are to separate the database and web server nodes onto different Elastic Cloud Servers (ECSs) and to enable automatic scaling of the web servers based on traffic demands.
1. Initial Network and Security Setup
The process begins by establishing a secure and isolated network environment. This is achieved by creating a Virtual Private Cloud (VPC) in the AP-Singapore region. A VPC provides a private, isolated virtual network, giving the user complete control over the virtual networking environment, including selecting their own IP address range, creating subnets, and configuring route tables and network gateways. A default subnet is created along with the VPC.
Following the VPC creation, a security group is configured. A security group acts as a virtual firewall for the ECS instances, controlling both inbound and outbound traffic. For this lab, a "General-purpose web server" template is used, which pre-configures rules to allow common web traffic on ports like HTTP (80), HTTPS (443), and ports for remote login (22 for SSH, 3389 for RDP). An additional inbound rule is added to allow all traffic from any IP address (0.0.0.0/0) to ensure full accessibility for the purpose of the lab, a practice that would be refined with more restrictive rules in a production environment.
2. Provisioning Compute and Database Resources
With the network in place, the next step is to provision the necessary compute and database resources. An Elastic Cloud Server (ECS) is purchased to host the web application. The configuration specifies a pay-per-use billing model, a general-purpose CentOS 7.6 64-bit image, and places it within the previously created VPC and security group. An Elastic IP (EIP) is auto-assigned to the ECS, providing it with a static public IP address necessary for internet access.
To fulfill the requirement of separating the database, a Relational Database Service (RDS) instance is procured. A MySQL 8.0 primary/standby instance is chosen to ensure high availability for the database layer. This instance is also placed within the same VPC and security group as the ECS, allowing secure communication between the web server and the database over the private network. A password for the 'root' user is set during this process, and the instance's floating IP address is noted for later use.
3. Web Application Deployment and Configuration
The lab then moves to software installation and configuration on the web server ECS. A remote VNC login is used to access the CentOS server's command line. The LAMP stack (Linux, Apache, MySQL, PHP) is installed using the yum package manager. The Apache HTTP server (httpd.conf) is configured by adding a ServerName directive.
The WordPress content management system is then deployed. The installation package is downloaded, extracted to the /var/www/html directory, and appropriate file permissions are set. The Apache (httpd) and php-fpm services are started and enabled to ensure they launch automatically on system boot.
A database for WordPress is created by logging into the RDS instance via the HUAWEI CLOUD console's Data Administration Service (DAS). A simple SQL command, create database wordpress;, is executed.
The final step is the WordPress installation wizard, accessed by navigating to the ECS's public IP address followed by /wordpress in a web browser. The wizard prompts for database connection details, including the database name (wordpress), username (root), password, and the RDS instance's floating IP address and port as the Database Host. Once the connection is established, the site title and an admin user are created, completing the WordPress setup.
4. Achieving High Availability with ELB and Auto Scaling
To meet the requirement for dynamic scaling, Elastic Load Balance (ELB) and Auto Scaling (AS) services are configured. A shared, public-facing load balancer is created within the VPC. A listener is configured on the ELB to listen for HTTP traffic on port 80 and forward it to a backend server group.
To enable Auto Scaling, a private image of the fully configured web server ECS is created using the Image Management Service (IMS). This image serves as a template for creating new ECS instances.
Next, an AS configuration is created, specifying the private image, instance type, and security group. Crucially, it's set not to assign a public EIP, as traffic will be routed through the ELB. An AS group is then defined, linking the AS configuration, the VPC, and the ELB. This group is configured with a minimum of 1, a maximum of 3, and an expected count of 2 instances.
Finally, AS policies are created to trigger scaling actions. An "add instance" policy is set to trigger if the CPU usage exceeds 60%, and a "reduce instance" policy is set for when the average CPU usage drops below 20%. The AS service automatically launches the expected number of instances, which appear in the ELB's backend server group.
5. Verification and Monitoring
The deployment is verified by accessing the WordPress site using the load balancer's EIP. The ability to view the site confirms that the entire architecture—from the load balancer through to the web servers and the backend database—is functioning correctly.
For ongoing management, the lab concludes by introducing the Cloud Eye service. Cloud Eye provides a centralized dashboard to monitor all deployed resources, view alarm statistics, and check detailed performance metrics for individual ECS instances, such as CPU usage, disk I/O, and network traffic. This allows administrators to observe the health and performance of their enterprise web application.

(<img width="913" height="564" alt="13" src="https://github.com/user-attachments/assets/13124435-67bf-4568-a827-a21dec7f8a3e" />
<img width="907" height="547" alt="12" src="https://github.com/user-attachments/assets/b3994f6f-98c7-4b61-8868-776a3dbc3eee" />
<img width="908" height="415" alt="11" src="https://github.com/user-attachments/assets/06c51574-6d51-40a1-afd6-14244a3a45d3" />
<img width="911" height="524" alt="10" src="https://github.com/user-attachments/assets/4ecbe5f7-ddf4-4501-91c9-8de5bd9880da" />
<img width="909" height="488" alt="9" src="https://github.com/user-attachments/assets/f0e2c439-a4ab-4bb0-bd8c-2604499ca2fa" />
<img width="906" height="397" alt="8" src="https://github.com/user-attachments/assets/a60c01d8-10cf-4d05-ba06-d4c004e91b06" />
<img width="910" height="422" alt="7" src="https://github.com/user-attachments/assets/f0defedc-96da-459e-9ee7-fa91a435d40e" />
<img width="909" height="418" alt="6" src="https://github.com/user-attachments/assets/495ee925-a329-465e-a09b-5ca5abdaa3a2" />
<img width="928" height="604" alt="5" src="https://github.com/user-attachments/assets/90cb6100-0449-4d4f-b850-25d20aed5905" />
<img width="915" height="453" alt="4" src="https://github.com/user-attachments/assets/71eb138d-fc0f-4c1c-8429-9f3d4c39b610" />
<img width="914" height="574" alt="3" src="https://github.com/user-attachments/assets/8cc30190-8a3c-4186-bc89-0ed05613591f" />
<img width="914" height="523" alt="2" src="https://github.com/user-attachments/assets/44396035-4734-41c0-86b8-6cc4b0990058" />
<img width="806" height="410" alt="1" src="https://github.com/user-attachments/assets/0c626442-c713-4763-8bff-dd0924be3695" />
<img width="906" height="433" alt="14" src="https://github.com/user-attachments/assets/c13fcc82-2aa4-44b4-8171-ee6a12705b08" />
)
