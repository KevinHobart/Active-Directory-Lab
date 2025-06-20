# Active-Directory-Lab

---

## Overview

This project demonstrates the comprehensive setup of an Active Directory home lab using virtualization (VirtualBox).  
The Active Directory home lab can then be used as a learning platform to simulate various IT workflows.  
The primary goals of this project are:

#### 1. Create two virtual machines on VirtualBox:
  - Windows 11
  - Windows Server 2022
#### 2. Configure Windows 11 VM:
  - Configure to allow connection with Active Directory domain.
#### 3. Configure Windows Server 2022 VM:
  - Add Active Directory service
  - Promote to Domain Controller
  - Add Users
#### 4. Configure network settings
#### 5. Join Windows 11 VM to Active Directory domain.

---

### Skills Learned

- **Virtualization:**
  - Properly allocate and manage hardware and networking resources when setting up and using a virtual machine.
- **Windows 11:**
  - Download, install, and configure Windows 11 to be used as the client (end user) machine in an Active Directory domain.
- **Windows Server 2022:**
  - Download, install, and configure Windows Server 2022 for use as an Active Directory Domain Controller.
- **Active Directory:**
  - Install and configure Active Directory Domain Services (AD DS) on Windows Server 2022, and promote to a Domain Controller.
  - Add Users to the domain.




### Tools and Technologies Used

- **Virtualization:**
  - VirtualBox 7.0.26
- **Operating Systems:**
   - Windows 11 (Client/User machine)  
   - Windows Server 2022 (Domain Controller)
- **Directory Service:**
  - Microsoft Active Directory Domain Services (AD DS)

---
---  

## A brief overview of Active Directory Domain Services from  Microsoft Learn:  

- A directory is a hierarchical structure that stores information about objects on a network. A directory service, such as Active Directory Domain Services (AD DS), provides the methods for storing directory data and making this data available to --network users and administrators. For example, AD DS stores information about user accounts, such as names, passwords, phone numbers, and so on. AD DS also provides a way for authorized users on the same network to access this information.

- AD DS stores information about objects on the network and makes this information easy for administrators and users to find and use. AD DS uses a structured data store as the basis for a logical, hierarchical organization of directory information.

- This data store, also known as the directory, contains information about AD DS objects. These objects typically include shared resources such as servers, volumes, printers, and the network user and computer accounts.

- Security is integrated with AD DS through sign-in authentication and access control to objects in the directory. With a single network username and password, administrators can manage directory data and organization throughout their network, and authorized network users can access resources anywhere on the network.
- Policy-based administration eases the management of even the most complex network.
- Link: [Active Directory Domain Services overview](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview)

## Steps for setting up the lab environment.  

This project consists of five components for setting up an Active Directory home lab environment.  
Here is a table of contents (including links) with recommended order of completion:
1. Downloading Windows 11 ISO and intalling on a VirtualBox VM. 




