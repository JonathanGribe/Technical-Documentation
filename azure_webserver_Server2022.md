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
Under ‘Project details’ will need to fill out each configuration information (Subscription, Resource group, etc…)
Refer to VM configuration table section at the end of the document for details
Refer to the ‘Value’ Column.  
--Whatever information is required it will be specified. 
-- Information with  “”   fill in with your own information. 
--Anything left blank can be ignored and skipped.



