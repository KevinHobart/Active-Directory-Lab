# Windows Server 2022 - Active Directory & Domain Controller Setup

This guide walks you through installing the Active Directory Domain Services (AD DS) role and promoting a Windows Server 2022 VM to a Domain Controller.

---

## Prerequisites

- A clean, installed **Windows Server 2022** VM.  Visit: [Windows-Server-2022-VM-setup](AD-Lab_Setup/Windows-Server-2022-VM-setup.md) if you have not installed Windows Server 2022.
- An **Administrator** password already set
- Internet access (for updates)

## Step 1:

1. Start VirtualBox
2. Select and **Start** the Windows Server 2022 VM
3. Login with the **Administrator** password you created for this server
4. **Server Manager** should automatically start and bring you to the Dashboard

---

## Step 2: Rename the Computer

1. In the search box, type **View your PC name**
   image 1
2. Click **Rename this PC** 
3. Rename the current PC.  Renaming to **DC01** follows a conventional naming practice, but you can rename to anything you like. 
4. Click **Next**
   image 2  
5. Click **Restart now** when prompted

---

## Step 3: Install the AD DS Role

1. Open **Server Manager** if it hasn't started automatically
   image 3
2. Click **Manage** > **Add Roles and Features**  
3. On the **Before You Begin** screen, click **Next**
   image 4  
4. Choose **Role-based or feature-based installation** > **Next**
   image 5 
5. Select your local server > **Next**
6. image 6 
7. Under **Server Roles**, check **Active Directory Domain Services**  
8. A dialog box will prompt you to add features. Click **Add Features**, Click **Next**
    images 7,8  
9. Click **Next** on *Features screen*
    image 9  
10. Click **Next** on *Active Directory Domain Services screen*
    image 10
11. On the *Confirm installtion selection* screen, Select the **Restart the destination server automatically if required** box.
12. Click **Install**
    image 11
13. Wait for installation to complete.

---

## Step 4: Promote Server to a Domain Controller

1. Once the AD DS role is installed, select **Promote this server to a domain controller** in the box under *additional steps are required to make this machine a domain controller*
   image 12

2. Select **Add a new forest**  
   - **Root domain name**: LAB.local
   - Note: you can name this whatever you like.  For example: ADLAB.local, ADServer.local, MyCompany.local, MyCompany.com, etc.
   - Click **Next**
   image 13
3. Set Directory Services Restore Mode (DSRM) **Password**, Click **Next**
   image 14 
4. Click **Next** through DNS Options and NetBIOS name screens
5. image 15, 16
6. Click **Next** through Paths screen
   image 17  
7. Review options and click **Next**
   image 18
8. Once the *Prerequisites Check* is done, you will see the green checkmark.  Ignore the yellow triangles.
     - Click **Install**  
     - The server will automatically reboot after installation
   image 19

---

## Step 5: Log into the Domain 
  
1. At the login screen, you should be able to login as **Administrator** on the domain you just created.  
   - Example: **LAB\Administrator**. Your's may differ, depending the the name you chose for your domain.
   - Login using the password you chose for **Administrator**
     image 20

---

## Step 6: Install the AD Certificate Services Role  
Active Directory Certificate Services (AD CS) is used to create certification authorities and related role services that allow you to issue and manage certificates used in a variety of applications.  
One of which is authenticating users.

1. Open **Server Manager** if it hasn't started automatically
   image 3
2. Click **Manage** > **Add Roles and Features**  
3. On the **Before You Begin** screen, click **Next**
   image 4  
4. Choose **Role-based or feature-based installation** > **Next**
   image 5 
5. Select your local server > **Next**
6. image 6 
7. Under **Server Roles**, check **Active Directory Certificates Services**  
8. A dialog box will prompt you to add features. Click **Add Features**, Click **Next**
    images 21, 22 
9. Click **Next** on *Features screen*  
10. Click **Next** on *Active Directory Certificate Services screen*
11. On the *Confirm installtion selection* screen, Select the **Restart the destination server automatically if required** box.
12. Click **Install**
    image 23
13. Wait for installation to complete.
14. Once the AD CS role is installed, select **Configure Active Directory Certificate Services on the destination server** in the box under *additional steps are required to configure Active Directory Certificate Services on the destination server*
    image 24
15. Click **Next** on *Credentials* Screen
16. Check **Certification Authority** box on *Role Services* Screen
    - Click **Next**
    image 25
17. Click **Next** on all other screens (defaults)
18. Click **Configure** on last screen
    image 26
19. Close all setup windows to get back to the Server Manager Dashboard

---

## Step 6: Verify AD DS and DNS Functionality

1. Open **Server Manager** (if not already open) 
2. Click **Tools** > **Active Directory Users and Computers**  
3. Confirm your domain (e.g., `LAB.local`) is listed  

5. Open **DNS** from Tools and check:
   - Forward Lookup Zones > `LAB.local`
   - _msdcs subdomain present
   image 27

---

## Optional: Create an Organizational Unit (OU) and a User

1. Open **Active Directory Users and Computers**  
2. Right-click the domain > **New > Organizational Unit**  
   - Name it: `TestOU`  
3. Right-click `TestOU` > **New > User**  
   - **First name**: John  
   - **Last name**: Doe  
   - **Username**: jdoe  
   - Set a password and deselect “User must change password at next logon”  
   - Click **Finish**

    **📷 Screenshot placeholder**

---

## Notes

- Restart your server after domain promotion and DNS changes  
- Snapshots are useful before/after making major changes  
- Always use strong passwords for administrative users  
- Practice creating GPOs, adding clients, or configuring DHCP next!

