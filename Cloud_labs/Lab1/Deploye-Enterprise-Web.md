# LAB: Deploying an Enterprise Web

An enterprise intends to deploy its website on HUAWEI CLOUD, and they have the 
following requirements:

1. Database nodes and service nodes are deployed on separate ECSs.
2.ECSs are added or removed as incoming traffic changes over time.

*Prerequisites*: Log in to HUAWEI CLOUD.Go to the [Lab Desktop] and open Google 
Chrome browser to access the HUAWEI CLOUD login page. Select IAM User Login. In the 
login dialog box, enter the assigned HUAWEI CLOUD lab account and password to log in to 
HUAWEI CLOUD, as shown in the following figure.

(![Huawei Lab Image](https://github.com/user-attachments/assets/c91de1db-01d9-44cc-9c69-378d473b4748)
)

Note: For details about the account information, please take a look at the upper part of the lab manual. Do not use Use 
your HUAWEI CLOUD account to log in. 
1. Tasks 
1.1 Creating a VPC 
Step 1: Switch to the management console and select the AP-Singapore region. In the left 
navigation pane, choose Service List > Networking > Virtual Private Cloud. 
Step 2: Click Create VPC. 
Step 3: Configure the parameters as follows, and click Create Now.

(![Lab2](https://github.com/user-attachments/assets/7b0bfaa5-5865-4d00-8647-f86489f54a00)
)

Step 2: Click Create VPC.

(![Lab3](https://github.com/user-attachments/assets/2bc4c9a5-39ee-40cb-9805-54de01afdc80)
)

Step 3: Configure the parameters as follows, and click Create Now. 
● Region: AP-Singapore 
● Name: vpc-mp (Change it as needed.) 
● Retain the default settings for other parameters. 

Step 4: View the created VPC in the VPC list. 

(![Lab4](https://github.com/user-attachments/assets/c94b9dd2-cbfe-4fff-bc00-05d2ffea92ae)
)


(![Lab5](https://github.com/user-attachments/assets/a5f32c88-e5d6-46b3-a9e2-777c6fafea51)
)

1.2 Creating and Configuring a Security Group 
Step 1: On the Network Console, choose Access Control > Security Groups and create a 
security group.

(![Lab6](https://github.com/user-attachments/assets/9a9b1b5a-5ccf-495c-8b34-26851e154b07)

Step 3: Click Inbound Rules and then Add Rule to add an inbound rule with the following 
parameter settings: 
● Protocol & Port: All 
● IP address in Source: 0.0.0.0/0

(![Lab7](https://github.com/user-attachments/assets/b67bcfcf-783a-43dd-bb95-02a14ef9681e)
)

1.3 Buying an ECS 
Step 1: In the service list, choose Compute > Elastic Cloud Server.

(![Lab8](https://github.com/user-attachments/assets/07bf30c8-b18a-4cc0-93b1-12480c3485d1)
)

Step 2: Click Buy ECS and set the following parameters. 
Basic settings: 
● Billing Mode: Pay-per-use 
● Region: AP-Singapore 
● AZ: Random 
● CPU Architecture: x86 
● Specifications: General computing, s6.small.1 1 vCPUs | 1 GB 
● Image: Public image, CentOS 7.6 64-bit (40 GB) 
● System Disk: High I/O, 40 GB 

(![Lab9](https://github.com/user-attachments/assets/469733ab-17a3-4ad8-b1d6-e6ced9a40c2c)
)

Network configuration: 
● Network: Select the VPC you have created. 
● Security Group: Select the security group you have created. 
● EIP: Auto assign, Dynamic BGP, Billed by Bandwidth, 2 Mbit/s

(![Lab10](https://github.com/user-attachments/assets/435d6b8d-d547-4c90-9f12-90a46fcf9e32)
)

Advanced settings: 
● ECS Name: ecs-mp (Change it as needed.) 
● Login Mode: Password, for example, Huawei@123! 
● Cloud Backup and Recovery: Not required

(![Lab11](https://github.com/user-attachments/assets/56a43daf-89b9-47ba-8385-826eed1c2e55)
)

1.4 Buying an RDS DB Instance 
Step 1: Go back to the service list, and choose Database > Relational Database Service.

(![Lab12](https://github.com/user-attachments/assets/3de1aa0f-309b-4f88-bf84-db150166a059)
)

Step 3: Set the parameters as follows and click Next. 
● Billing Mode: Pay-per-use 
● Region: AP-Singapore 
● Instance parameters: rds-name (customizable), MySQL, 8.0, Primary/Standby, Cloud SSD 
● Performance specifications: 2 vCPUs | 4 GB. Determine the specifications based on real-world 
service requirements. 
● VPC, Security Group, and Password: Select the VPC and security group you have created. 
Set the password, for example, Huawei!@#$.

(![Lab13](https://github.com/user-attachments/assets/7f808458-1b70-428b-96a9-8d8dce316c6a)
)

Step 4: Confirm the configuration, and click Submit. Go to the RDS DB instance list, and wait 
for the creation to complete, which takes 6 to 10 minutes.

(![Lab14](https://github.com/user-attachments/assets/3bb6ac0b-dba5-4ffd-8134-e32e978bbed4)
)

(![Lab15](https://github.com/user-attachments/assets/15f71cf0-88d0-4eaa-93f9-66379b406011)
)

Step 3: Run the following command to install LAMP and enable the services you will need: 
Copy Codeyum install -y httpd php php-fpm php-mysql mysql

(![Lab16](https://github.com/user-attachments/assets/c3865a10-b36f-451d-9cd1-48211408ff8d)
)

Step 4: Configure httpd: 
Copy Codevim /etc/httpd/conf/httpd.conf

(![Lab17](https://github.com/user-attachments/assets/a1804c6f-d2fe-4bb4-abaa-15e7a73f24ad)
)

Step 5: In the configuration file, press Shift+G to go to the last line of the configuration file, 
press I to enter editing mode, move the cursor to the end of the configuration file, and press 
Enter. Then copy and paste the following content: 
Copy CodeServerName localhost:80 


(![Lab18](https://github.com/user-attachments/assets/d1d6ba15-771c-4304-b104-b5fb29fe6589)
)

Step 8: Run the following command to decompress the WordPress installation package to the 
/var/www/html directory: 
Copy Codetar -zxvf wordpress-4.9.10.tar.gz -C /var/www/html 
The command output, similar to the following, is displayed.

(![Lab19](https://github.com/user-attachments/assets/050caf21-4c75-4712-82e3-93737db673f0)
)

Step 12: Run the following command to check the httpd status, which should be active (running) 
and highlighted: 
Copy Codesystemctl status httpd

(![Lab20](https://github.com/user-attachments/assets/77e6616d-e999-4885-b7bb-8124c00f36ef)
)

Step 15: Run the following command to configure php-fpm to automatically start upon system boot. 
If information similar to what is shown in the figure is displayed, PHP-FPM has been configured to 
automatically start upon system boot. 
Copy Codesystemctl enable php-fpm 

(![Lab21](https://github.com/user-attachments/assets/b3125c84-6d66-44bd-a178-855dc5b89175)
)

Step 4: Enter the following SQL statement and click Execute SQL. If the following information 
is displayed, the database for WordPress has been created. 
Copy Code create database WordPress 

(![Lab22](https://github.com/user-attachments/assets/0786b9e2-5839-4b84-8445-57ce03382094)
)

Figure 1-3 Opening the WordPress installation wizard 
Step 2: Click Let's go!. In the displayed page, enter the database access information, and click 
Submit. 
● Database Name: WordPress 
● Username: root 
● Password: Enter the password you set. 
● Database Host: Enter the database floating IP address and port number obtained in the section 
Buying an RDS DB Instance. 
● Table Prefix: Retain the default settings.

(![Lab23](https://github.com/user-attachments/assets/36a1a77c-3c8b-4c41-8f69-1e046ee1f4ac)
)

(![Lab24](https://github.com/user-attachments/assets/7063ceb4-5fa0-4408-922d-92c5052307fe)
)

(![Lab25](https://github.com/user-attachments/assets/672cc41c-ba67-47e4-88fb-974192c0a929)
)

(![Lab26](https://github.com/user-attachments/assets/0c841cfb-e03d-4505-9d9a-d478c886d7c2)
)

(![Lab27](https://github.com/user-attachments/assets/7f6e5e20-a5d8-46f6-a4fd-1053b09fea61)
)

(![Lab28](https://github.com/user-attachments/assets/305fe10e-7a02-4c0e-8a18-702b4aa28637)
)

(![Lab29](https://github.com/user-attachments/assets/366865e2-09e3-4429-905c-04b1bd456341)
)

(![Lab30](https://github.com/user-attachments/assets/0103ad3a-d00b-4ea4-adfa-44d7d50844e8)
)

(![Lab31](https://github.com/user-attachments/assets/83fa7716-c5dd-4a6f-9086-401f4cde005a)
)

(![Lab32](https://github.com/user-attachments/assets/d336aa0e-7bbb-46db-875b-6a17e0c8ee47)
)

(![Lab33](https://github.com/user-attachments/assets/cdd59f86-1563-4518-8021-6fed19e5c6de)
)

# LAB: Deploying an Enterprise Web End.
