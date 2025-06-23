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
  - Download, install, and configure Windows Server 2022 for use as an Active Directory Domain Controller (using Server Manager).
- **Active Directory:**
  - Install and configure Active Directory Domain Services (AD DS) on Windows Server 2022, and promote to a Domain Controller.
  - Add Users to the domain.
- **NAT and DNS**
  - Configure a NAT Network with static IP adresses. Configure DNS on server VM (it will need to resolve hostnames inside of our network).

---

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

## Steps for creating and setting up the lab environment.  

This project consists of five components for setting up an Active Directory home lab environment.  
The following is a table of contents in the recommended order of completion:  

1. Downloading and installing Windows 11 ISO (VirtualBox).
   - [AD-Lab_Setup/Windows11-VM-setup.md](https://github.com/KevinHobart/Active-Directory-Lab/blob/main/AD-Lab_Setup/Windows11-VM-setup.md)
2. Downloading and installing Windows Server 2022 ISO (VirtualBox).
   - [AD-Lab_Setup/Windows-Server-2022-VM-setup.md](https://github.com/KevinHobart/Active-Directory-Lab/blob/main/AD-Lab_Setup/Windows-Server-2022-VM-setup.md)
3. Install Active Directory Domain Services on the Windows Server 2022 VM, and promote to a Domain Controller.
   - [AD-Lab_Setup/Config-Server-as-AD-Domain-Controller.md](https://github.com/KevinHobart/Active-Directory-Lab/blob/main/AD-Lab_Setup/Config-Server-as-AD-Domain-Controller.md)
4. Configure Network settings: Setting up NAT Network and DNS.
   - [AD-Lab_Setup/Configure-Network-Settings.md](https://github.com/KevinHobart/Active-Directory-Lab/blob/main/AD-Lab_Setup/Configure-Network-Settings.md)
5. Joining the Windows 11 VM to the Active Directory domain.
   - [AD-Lab_Setup/Join-Windows11-VM-to-Domain.md](https://github.com/KevinHobart/Active-Directory-Lab/blob/main/AD-Lab_Setup/Join-Windows11-VM-to-Domain.md)

---
---

# Project steps:
Listed below are summaries of each step for completing this project.  The link in each step will take you to full tutorial page for that step.  When all steps have been completed, you will have successfuly set up a basic Active Directory home lab, consisting of:  
 - Windows 11 client machine.
 - Windows server 2022 with Active Directory Domain Services installed.
 - One domain user, and a domain administrator (sysadmin).
     
There are many projects that can be completed using this home lab, including: 
 - Creating and managing users.
 - Creating and managing groups.
 - Configuring and managing OUs (Organizational Units).
 - Setting up and enforcing various policies.  

---

### 1. 💻[Downloading Windows 11 ISO and Installing on a VirtualBox VM.](https://github.com/KevinHobart/Active-Directory-Lab/blob/main/AD-Lab_Setup/Windows11-VM-setup.md)

- Download the Windows 11 Enterprise ISO from the official Microsoft Evaluation Center.  
- Create a new VM in VirtualBox with recommended resources (4 GB+ RAM, 2+ CPUs).  
- Complete the Windows 11 setup process with standard settings and licensing terms.  
- Install Guest Additions to enable proper VM integration.  
- Create an initial snapshot after installation for quick restore points.

---

### 2. 💻[Downloading Windows Server 2022 and Installing on a VirtualBox VM](https://github.com/KevinHobart/Active-Directory-Lab/blob/main/AD-Lab_Setup/Windows-Server-2022-VM-setup.md)

- Download Windows Server 2022 ISO from Microsoft Evaluation Center.  
- Create a new VirtualBox VM with recommended resources (8 GB RAM, 2–4 CPUs).  
- Install Windows Server 2022 Standard (Desktop Experience).  
- Set an Administrator password after first boot and complete setup.  
- Install VirtualBox Guest Additions and take an intial snapshot for recovery.

---

### 3. 🗃️[Installing Active Directory Domain Services and Promoting to a Domain Controller](https://github.com/KevinHobart/Active-Directory-Lab/blob/main/AD-Lab_Setup/Config-Server-as-AD-Domain-Controller.md)

- Log in to your Server VM as the Administrator and open Server Manager.  
- Add the Active Directory Domain Services (AD DS) role and complete feature installation.  
- Promote the server to a Domain Controller and configure the desired domain name.  
- Set a Directory Services Restore Mode (DSRM) password during promotion.  
- Restart the server after promotion — it will now serve as the Domain Controller.

---

### 4. 🔄[Configuring Network Settings (NAT Network and DNS)](https://github.com/KevinHobart/Active-Directory-Lab/blob/main/AD-Lab_Setup/Configure-Network-Settings.md)

- Configure both the Server and Windows 11 VM to use a **NAT Network** in VirtualBox.  
- Assign a static IP address to the Domain Controller VM and set its DNS to its own IP address.  
- Assign a static IP to the Windows 11 VM and configure its DNS to point to the Domain Controller.  
- Test basic connectivity by pinging the server’s IP and verifying DNS resolution.  
- Save a snapshot of both VMs after setup for an easy restore point if anything goes wrong.

---

### 5. ↔️[Joining the Windows 11 VM to the Domain and Creating a User](https://github.com/KevinHobart/Active-Directory-Lab/blob/main/AD-Lab_Setup/Join-Windows11-VM-to-Domain.md)

- Verify that the Windows 11 VM can resolve the domain and can ping the Domain Controller.  
- Rename the Windows 11 VM, then join it to the Active Directory domain.  
- Restart the Windows 11 VM and log in as the local Administrator after joining.  
- On the Server VM, create a new Active Directory user in **Active Directory Users and Computers**.  
- Log in to the Windows 11 VM with the new domain user credentials to confirm successful setup.







