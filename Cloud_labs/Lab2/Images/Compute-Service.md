HUAWEI CLOUD Compute Service
Overview
This guide demonstrates how to deploy and manage Elastic Cloud Servers (ECS) using HUAWEI CLOUD's infrastructure services, with a focus on creating and utilizing custom images through the Image Management Service (IMS).

1. Initial Setup and ECS Deployment
Network Foundation
Create a Virtual Private Cloud (VPC):
Provides isolated network environment
Configure IP ranges and subnets
Set up route tables and gateways
Server Provisioning
Deploy two server types with distinct configurations:

Windows ECS
Image: Windows Server 2012 R2 (public image)
Configuration:
Billing: Pay-per-use
Region: AP-Singapore
No Elastic IP (EIP) assigned initially
Set administrator password during creation
Linux ECS
Image: CentOS 7.6 (public image)
Configuration:
Auto-assign Elastic IP
Same region and billing model
Set root password during creation
Server Management
Access Methods:

Windows: Remote Desktop via VNC client
Linux: Command line via VNC terminal (user: root)
Resource Modification:

Stop the ECS instance
Select "Modify Specifications"
Choose new hardware configuration
Restart to apply changes
2. Image Management Service (IMS)
Creating Private Images
Transform configured ECS instances into reusable templates:

Windows Image Preparation
Network Configuration:
Set NIC to DHCP (automatic IP/DNS)
Remote Access:
Enable Remote Desktop
Configure firewall rules
Initialization:
Verify Cloudbase-Init installation
Linux Image Preparation
Network Configuration:
Ensure DHCP in network config files
Initialization:
Confirm Cloud-Init and password reset plugin
Cleanup:
Remove persistent network rules (/etc/udev/rules.d)
Image Creation Process
Navigate to IMS console
Select "Create System Disk Image"
Choose prepared ECS as source
Configure image metadata (name, description)
3. Advanced Image Operations
Image Management
Metadata Editing: Update names/descriptions
Regional Replication: Create copies within same region
Version Control: Maintain multiple image versions
Image Sharing
Obtain recipient's Project ID
Select "Share" on private image
Add recipient's Project ID
Recipient accepts shared image in their account
Deployment from Custom Images
Launch new ECS instance
Select your private image as source
Configure instance parameters
Deploy identical environment in minutes
Best Practices
Security: Always remove sensitive data before imaging
Documentation: Maintain change logs for custom images
Testing: Validate new images in staging before production
Tagging: Use consistent naming conventions for images


