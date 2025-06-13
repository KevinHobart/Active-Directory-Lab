# Windows Server 2022 - Active Directory & Domain Controller Setup

This guide walks you through installing the Active Directory Domain Services (AD DS) role and promoting a Windows Server 2022 VM to a Domain Controller.

---

## Prerequisites

- A clean, installed **Windows Server 2022** VM.  Visit: [Windows-Server-2022-VM-setup](AD-Lab_Setup/Windows-Server-2022-VM-setup.md) if you have not installed Windows Server 2022.
- An **Administrator** password already set
- Internet access (for updates)

---



---

## Step 2: Rename the Computer

1. Open **Server Manager**  
2. Click **Local Server** on the left  
3. Next to **Computer Name**, click the current name to open **System Properties**  
4. Click **Change…**, rename your server (e.g., `DC1`), then click OK  
5. Restart when prompted

   **📷 Screenshot placeholder**

---

## Step 3: Install the AD DS Role

1. Open **Server Manager**  
2. Click **Manage** > **Add Roles and Features**  
3. On the **Before You Begin** screen, click **Next**  
4. Choose **Role-based or feature-based installation** > **Next**  
5. Select your local server > **Next**  
6. Under **Server Roles**, check **Active Directory Domain Services**  
7. A dialog box will prompt you to add features. Click **Add Features**  
8. Click **Next** on Features screen  
9. Click **Next** on AD DS screen  
10. Click **Install**

    **📷 Screenshot placeholder**

11. Wait for installation to complete.

---

## Step 4: Promote Server to a Domain Controller

1. Once the AD DS role is installed, click the **flag icon** in Server Manager > **Promote this server to a domain controller**

2. Choose **Add a new forest**  
   - **Root domain name**: e.g., `lab.local`

3. Set Directory Services Restore Mode (DSRM) password  
4. Click **Next** through DNS Options and NetBIOS name  
5. Click **Next** through Paths  
6. Review options and click **Install**

    **📷 Screenshot placeholder**

---

## Step 5: Restart and Log into the Domain

1. The server will automatically reboot after installation  
2. At login screen, select **Other user**  
3. Log in as:  
   - **Username**: `lab\Administrator`  
   - **Password**: (the one you originally set)

    **📷 Screenshot placeholder**

---

## Step 6: Verify AD DS and DNS Functionality

1. Open **Server Manager**  
2. Click **Tools** > **Active Directory Users and Computers**  
3. Confirm your domain (e.g., `lab.local`) is listed  
4. Explore built-in OUs (Organizational Units)

5. Open **DNS** from Tools and check:
   - Forward Lookup Zones > `lab.local`
   - _msdcs subdomain present

    **📷 Screenshot placeholder**

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

