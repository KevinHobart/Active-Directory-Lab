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
   ![1rename](https://github.com/user-attachments/assets/02f6db60-e3fb-4c79-97f1-7e04bd24927a)

2. Click **Rename this PC** 
3. Rename the current PC.  Renaming to **DC01** follows a conventional naming practice, but you can rename to anything you like. 
4. Click **Next**
    ![2rename](https://github.com/user-attachments/assets/a6b3212b-2969-40c9-b3f5-bbfc0c9eed3a)

5. Click **Restart now** when prompted

---

## Step 3: Install the AD DS Role

1. Open **Server Manager** if it hasn't started automatically
   ![3installAD](https://github.com/user-attachments/assets/0d5486ef-80df-40e8-95d5-feab09eb620e)

2. Click **Manage** > **Add Roles and Features**  
3. On the **Before You Begin** screen, click **Next**
   ![4installAD](https://github.com/user-attachments/assets/b094760f-bef4-448e-9e43-64cd601976f7)

4. Choose **Role-based or feature-based installation** > **Next**
    ![5installAD](https://github.com/user-attachments/assets/f15866a2-75b3-4eda-ab4a-85d72b1a1297)

5. Select your local server > **Next**
    ![6installAD](https://github.com/user-attachments/assets/93b0ca39-8980-49c8-9109-a0ed6f579a03)

6. Under **Server Roles**, check **Active Directory Domain Services**  
7. A dialog box will prompt you to add features. Click **Add Features**, Click **Next**
      ![7installAD](https://github.com/user-attachments/assets/a4a231fd-2c7e-43b7-a1f5-a5f301a83edd)
      ![8installAD](https://github.com/user-attachments/assets/742e1260-5b07-4719-b25d-4f568ebd7149)

8. Click **Next** on *Features screen*
      ![9installAD](https://github.com/user-attachments/assets/1e9eb464-beea-47b9-8887-c51e8c8512e7)
 
9. Click **Next** on *Active Directory Domain Services screen*
    ![10installAD](https://github.com/user-attachments/assets/c8c3509e-bb4e-4147-bc25-cdca94ab3b00)

10. On the *Confirm installtion selection* screen, Select the **Restart the destination server automatically if required** box.
11. Click **Install**
    ![11installAD](https://github.com/user-attachments/assets/752e78e0-2a22-48ac-a88e-3c0b4ef3ab93)

12. Wait for installation to complete.

---

## Step 4: Promote Server to a Domain Controller

1. Once the AD DS role is installed, select **Promote this server to a domain controller** in the box under *additional steps are required to make this machine a domain controller*
   ![12promote](https://github.com/user-attachments/assets/d5166233-3c5e-43f7-b897-cb4cc006d039)

2. Select **Add a new forest**  
   - **Root domain name**: LAB.local
   - Note: you can name this whatever you like.  For example: ADLAB.local, ADServer.local, MyCompany.local, MyCompany.com, etc.
   - Click **Next**
   ![13promote](https://github.com/user-attachments/assets/655502e1-d4f2-4ef7-83e9-71a0e08db6f3)

3. Set Directory Services Restore Mode (DSRM) **Password**, Click **Next**
   ![14promote](https://github.com/user-attachments/assets/ae6b18ba-69f2-47c8-987c-dacfbe0adc6e)

4. Click **Next** through DNS Options and NetBIOS name screens
   ![15promote](https://github.com/user-attachments/assets/7a6171ce-73b8-483f-a0c6-9be18efad343)
   ![16promote](https://github.com/user-attachments/assets/51b20162-1709-4dab-85ed-62cd7fbf2775)

5. Click **Next** through Paths screen
   ![17promote](https://github.com/user-attachments/assets/b74f3f6d-39ae-41d7-9bef-9658798b7590)

6. Review options and click **Next**
   ![18promote](https://github.com/user-attachments/assets/3140e5de-8a14-409d-9bb5-518940d528cb)

7. Once the *Prerequisites Check* is done, you will see the green checkmark.  Ignore the yellow triangles.
     - Click **Install**  
     - The server will automatically reboot after installation
   ![19promote](https://github.com/user-attachments/assets/54e4a565-1582-4062-bb18-dfc652febb22)


---

## Step 5: Log into the Domain 
  
1. At the login screen, you should be able to login as **Administrator** on the domain you just created.  
   - Example: **LAB\Administrator**. Your's may differ, depending the the name you chose for your domain.
   - Login using the password you chose for **Administrator**
     ![20login](https://github.com/user-attachments/assets/8bd9173a-ee99-4541-9efc-1d756d3fdce6)


---

## Step 6: Install the AD Certificate Services Role  
Active Directory Certificate Services (AD CS) is used to create certification authorities and related role services that allow you to issue and manage certificates used in a variety of applications.  
One of which is authenticating users.

1. Open **Server Manager** if it hasn't started automatically
   ![3installAD](https://github.com/user-attachments/assets/28ccf449-b689-4587-8900-eddb29d27300)

2. Click **Manage** > **Add Roles and Features**  
3. On the **Before You Begin** screen, click **Next**
   ![4installAD](https://github.com/user-attachments/assets/b22099f7-703a-4a08-b793-a8c82cc37894)
 
4. Choose **Role-based or feature-based installation** > **Next**
   ![5installAD](https://github.com/user-attachments/assets/37c10401-0909-478c-87b6-d057df300da3)

5. Select your local server > **Next**
    ![6installAD](https://github.com/user-attachments/assets/01b19764-c016-44a6-b20b-c676511a090b)

6. Under **Server Roles**, check **Active Directory Certificates Services**  
7. A dialog box will prompt you to add features. Click **Add Features**, Click **Next**
    ![21ADCS](https://github.com/user-attachments/assets/aa517b1b-d663-49bc-b714-f20b1299f657)
    ![22ADCS](https://github.com/user-attachments/assets/36a70403-5489-4435-aeaf-404ee135f81d)

8. Click **Next** on *Features screen*  
9. Click **Next** on *Active Directory Certificate Services screen*
10. On the *Confirm installtion selection* screen, Select the **Restart the destination server automatically if required** box.
11. Click **Install**
    ![23ADCS](https://github.com/user-attachments/assets/f146c83a-1322-4522-b410-6e3767c43cf6)

12. Wait for installation to complete.
13. Once the AD CS role is installed, select **Configure Active Directory Certificate Services on the destination server** in the box under *additional steps are required to configure Active Directory Certificate Services on the destination server*
    ![24ADCS](https://github.com/user-attachments/assets/e8c136ac-2962-4d8b-be8e-ae0b810850ed)

14. Click **Next** on *Credentials* Screen
15. Check **Certification Authority** box on *Role Services* Screen
    - Click **Next**
    ![25ADCS](https://github.com/user-attachments/assets/d2bc7dbc-e923-4f00-9259-f2451951a0af)

16. Click **Next** on all other screens (defaults)
17. Click **Configure** on last screen
    ![26ADCS](https://github.com/user-attachments/assets/bccc4d71-2f34-44d5-ad4f-5f658fb41b6e)

18. Close all setup windows to get back to the Server Manager Dashboard

---

## Step 6: Verify AD DS and DNS Functionality

1. Open **Server Manager** (if not already open) 
2. Click **Tools** > **Active Directory Users and Computers**  
3. Confirm your domain (e.g., `LAB.local`) is listed  

4. Open **DNS** from Tools and check:
   - Forward Lookup Zones > `LAB.local`
   - _msdcs subdomain present
   ![27DNS](https://github.com/user-attachments/assets/641179b9-51ca-42c6-b163-3e175966ccc2)


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

