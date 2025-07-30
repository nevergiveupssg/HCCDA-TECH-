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

Note: For details about the account information, see the upper part of the lab manual. Do not use Use Use 
your HUAWEI CLOUD account to log in. 
1. Tasks 
1.1 Creating a VPC 
Step 1: Switch to the management console and select the AP-Singapore region. In the left 
navigation pane, choose Service List > Networking > Virtual Private Cloud. 
Step 2: Click Create VPC. 
Step 3: Configure the parameters as follows, and click Create Now.

(![Lab2](https://github.com/user-attachments/assets/7b0bfaa5-5865-4d00-8647-f86489f54a00)
)

Step 2 Click Create VPC.
(![Lab3](https://github.com/user-attachments/assets/2bc4c9a5-39ee-40cb-9805-54de01afdc80)
)

Step 3 Configure the parameters as follows, and click Create Now. 
● Region: AP-Singapore 
● Name: vpc-mp (Change it as needed.) 
● Retain the default settings for other parameters. 

Step 4 View the created VPC in the VPC list. 

(![Lab4](https://github.com/user-attachments/assets/c94b9dd2-cbfe-4fff-bc00-05d2ffea92ae)
)

(![Lab5](https://github.com/user-attachments/assets/a5f32c88-e5d6-46b3-a9e2-777c6fafea51)
)
1.2 Creating and Configuring a Security Group 
Step 1 On the Network Console, choose Access Control > Security Groups and create a 
security group.
