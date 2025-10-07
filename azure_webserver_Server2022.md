# Setup Guide - Azure Webserver (Windows Server 2022)

## Introduction:
By the end of this lab, you will be able to set up a web server using Azure virtual machine and Windows Server 2022
Purpose: 
This is a guide to setting up and hosting a website using Internet Information Services (IIS) on Windows Server 2022. From the student perspective it is to build familiarity with the platform in order to develop higher level skills later.
________________________________________
## Prerequisites:
•	Knowing how to do basic computer navigation 
•	Familiarity in Azure Portal is recommended
________________________________________
## Platforms and Environment
Environment:
•	Microsoft Azure (https://portal.azure.com)
•	Windows Server 2022 - Datacenter - x64 Gen2
________________________________________
## Setup Overview:
1.	Create Virtual Machine(VM) with Windows Server 2022 - Datacenter - x64 Gen2 image
2.	Installation of IIS on VM
3.	Add website using IIS manager

### Create Virtual Machine with Windows Server 2022
**Step 1: Getting Started**
1.	Log into Microsoft Azure Portal (https://portal.azure.com)
2.	Click the menu icon (top-left) to drop down menu

<img width="394" height="59" alt="image" src="https://github.com/user-attachments/assets/bf83501e-1385-4085-8d43-9f0368655d27" />

3.	Select  ‘Virtual Machines’ in the menu

<img width="352" height="1214" alt="image" src="https://github.com/user-attachments/assets/0121f51d-aa02-439d-a6a3-289841a4cb4f" />

4.	Select ‘Create’ in the mid-left and select ‘Virtual machine’

<img width="572" height="836" alt="image" src="https://github.com/user-attachments/assets/c9f1653b-a7ad-4937-83c8-36aa6c6f1127" />

**Step 2: Virtual Machine Configuration**
1. Under ‘Project details’ will need to fill out each configuration information (Subscription, Resource group, etc…)
2. Refer to VM configuration table section at the end of the document for details
3. Refer to the ‘Value’ Column.  
--Whatever information is required it will be specified. 
-- Information with  “”   fill in with your own information. 
--Anything left blank can be ignored and skipped.

**Step 3: Connect to the Virtual Machine using RDP**
1. Navigate toAzure Virtual Machine’s Overview Page 
2. Select ‘Connect’ 
3. Click ‘Connect via RDP and  ‘ Download RDP file

<img width="975" height="538" alt="image" src="https://github.com/user-attachments/assets/6032f938-5fa4-4cce-8fa5-05bdb5a18699" />

4.	Where you saved the file, double click and click ‘connect’
5.	Type password
6. Select ‘Yes’ option when asking for a certificate


## Install Internet Information Services
**Step 1: Installing Information Services in AD**
1. Upon bootup Server Manager should load
- If it does not load search ‘Server Manager’ bottom left by the Windows icon
2. Select ‘Add roles and features’ on the Dashboard
3. Click ‘Next’ and make sure ‘Role-based or feature-based installation’ is selected

<img width="975" height="691" alt="image" src="https://github.com/user-attachments/assets/6d2f869a-4cce-4432-ab64-b64586eca59b" />

4. Select Destination Server - Since we only have one server select ‘Next’

<img width="975" height="689" alt="image" src="https://github.com/user-attachments/assets/c3d06c55-f15e-4a0d-913a-5425a9b1c142" />

5. Server Roles - Scroll down to find ‘ Web Server (IIS). Select this option and ‘Add Features’

<img width="975" height="686" alt="image" src="https://github.com/user-attachments/assets/c8bc1cdf-4206-45ad-bbe4-aa31df94a611" />

6. Click ‘Next’ through the rest of the setup process and click ‘Install’ at the Confirmation screen

<img width="975" height="695" alt="image" src="https://github.com/user-attachments/assets/342f9436-1a05-4c56-824b-3b26b71961c4" />

**Step 2: Add rule to the VM Network Security Group**
Although Windows Server (IIP management) maybe correctly configured we need to allow web traffic through the Azure Firewall (Network Security Group)
1. Select the Network drop-down in left menu
2. Click ‘Network settings’
3. Scroll down until you get see ‘Rules’ to the right click ‘Create port rule’
4. Select ‘Inbound port rule’
5. Under ‘Service’ select ‘HTTP’ and ‘Add’
6. If it asks for a name just type: AllowHTTP

Verify Server is working:
1. Take the VMs public IP address and put it into the browser 
2. Should populate with the IIS website as shown below:

<img width="975" height="677" alt="image" src="https://github.com/user-attachments/assets/53b75784-6cf4-4b21-9b58-83859b0f62fa" />

## Adding Custom Website
**Step 1: Gather/Create web files to be used for the website**
1. Find a way to transfer you html/css files to windows server2022
**Step 2: Adding Website to the C:\inetpub folder**
1. Search 'File Explorer' in the search box and open
2. In the 'Address bar' at the top type the path 'C:\inetpub'
3. Create a new folder. Call the folder something related to what the website is about
   - In this particular case we will name it 'ArtPortfolio'
<img width="975" height="339" alt="image" src="https://github.com/user-attachments/assets/c4e34af9-2529-400f-b2da-79847fbeace3" />

4. Place files in folder
   - Name the homepage of the website index.html
  
<img width="975" height="197" alt="image" src="https://github.com/user-attachments/assets/4fb16d35-aa8d-46cd-81a9-8c69626c947d" />

**Step 3: Add the website to IIS manager**
1. Left side of IIS manager, right-click on server name
2. Click 'Add website'

<img width="452" height="256" alt="image" src="https://github.com/user-attachments/assets/26b27f7f-e415-42ab-9efb-58161feb3692" />

3. In the Add Website window add the Site name and Physical path C:\inetpub\the-folder-you-created
   - In the example, the path is C:\inetpub\ArtPortfolio
   <img width="922" height="1056" alt="image" src="https://github.com/user-attachments/assets/d84d665e-1949-4a3c-aafa-d164f03a945f" />

Step 4: Verifying website is online
1. Open up a web browser on Server 2022
2. Type http://localhost into the address bar
   - If successful, will show website
   - If not successful refer to the troubleshooting steps below
  
Example website:

<img width="975" height="437" alt="image" src="https://github.com/user-attachments/assets/cdf47a2f-658b-4178-9192-d0a191839228" />

## Troubleshooting

**Issue: If the IIS page doesn’t load:**
1. Check that the HTTP port rule is added in the Network Security Group
2. Ensure the VM is running and the public IP is correct
   
**Issue: If RDP fails to login:**
1. Verify that port 3389 is open
2. Confirm your credentials and IP address
   
**Issue: If Website is not loading**
1. Ensure that the page is named index.html

## Azure Virtual Machine Configurations (For Step 1 – Getting Started):

Section	Name	Value
Basics	Subscription	""
 	Resource Group	""
 	Virtual Machine Name	""
 	Region	Whichever region is closes to you
 	Availability Options	 
 	Security Type	Standard
 	Image	Windows Server 2022 - Datacenter - x64 Gen2 (Click 'See all images' and under 'Market Place' type into the search field the image name)
 	Size	Standard D4as v6 (4 vcpus, 16 GiB memory)
 	Username	""
 	Password	""
 	Inbound Port Rules	 
Disks	OS Disk Type	Premium SSD (locally-redundant storage)
 	Encryption Type	 
 	Data Disks	 
 	Host Caching	 
 	Ephemeral OS Disk	 
Networking	Virtual Network (VNet)	 
 	Subnet	 
 	Public IP Address	 
 	NIC Network Security Group	 
 	Accelerated Networking	 
 	Load Balancing	 
Management	Monitoring	 
 	Identity	 
 	Auto-shutdown	 
 	Backup	 
 	Guest OS Updates	 
Advanced	Extensions	 
 	Custom Data	 
 	Host Group	 
 	Proximity Placement Group	 
 	VM Generation	 
Tags	Name / Value Pairs	 












