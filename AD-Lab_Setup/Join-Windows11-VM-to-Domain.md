# Join Windows 11 VM to the Domain & Create a Domain User

This tutorial will be the final tutorial for setting up an Active Directory home lab. It will provide steps on how to join a Windows 11 VM to your Active Directory domain, and then how to create a new domain user for login. Ensure both your **Windows Server 2022 Domain Controller** and **Windows 11 Client** are powered on, connected to the same network, and properly configured.

---

## Step 1: Verify Network Connectivity

1. On the **Windows 11 Client VM**, open **Command Prompt** and ping the domain controller.

   ```bash
   ping lab.local
   ```

   Replace `lab.local` with your actual domain name.

   - If the ping is successful, proceed.
   - If not, check your network settings and DNS configuration.

   📸 *Insert screenshot 1

---

## Step 2: Rename the Windows 11 PC
Before joining the Windows 11 VM to the domain, you'll want to rename the PC so it is easily identifiable when viewed on the domain controller.  
- A good naming convention would be **WS01**.  This denotes it as Workstation 01.
- In the future, you can add more machines and continue with the naming scheme - WS02, WS03....WS21, and so on.
  
1. On the **Windows 11 Client VM**:
   - Open **Settings > System > About**
   - Click **Rename this PC**

   📸 *Insert screenshot of the "About" page with the rename link.*

2. Enter the new name: `WS01`

3. Click **Next**, then **Restart now** when prompted.

   📸 *Insert screenshot 2

4. After restart, verify the name change by opening **Command Prompt** and typing:

   ```bash
   hostname
   ```

   It should return `WS01`.

---

## Step 3: Join Windows 11 to the Domain

1. On the **Windows 11 Client VM**:
   - Search for and select: **Access work or school**

2. Click **Connect**
   - Select **Join this device to a local Active Directory domain** in the pop up window.

   📸 *Insert screenshot 3

4. Enter your domain name (e.g., `LAB.local`).
   - Click **Next**
   Image 4
   
6. Enter credentials for the domain user with permission to join the domain (this will be the administrator password you created to login to the server/domain controller):
   - **Username**: `administrator`
   - **Password**: *(your domain admin password)*
   Image 5
7. Leave defaults on the *Add an account* window
   - Click **Next**
   Image 6
8. You will be prompted to restart. Click **Restart now**

---

## Step 4: Verify Domain Join

1. After reboot, on the **login screen**, click **Other user**.

2. Log in with:
   - **Username**: `yourdomain\username` (e.g., `dc01\Administrator`)
   - **Password**: *(domain password)*

   📸 *Insert screenshot of login screen with domain user selected.*

3. You should now be logged into the domain.

---

## Step 5: Create a New Domain User (on Server)

1. On the **Windows Server 2022 Domain Controller**:
   - Open **Server Manager**
   - Click **Tools > Active Directory Users and Computers**

   📸 *Insert screenshot of Server Manager with ADUC opened.*

2. In the left pane, expand your domain and right-click the **Users** folder.

3. Choose **New > User**.

   📸 *Insert screenshot of the New User wizard.*

4. Fill out the required fields:
   - **First name**: John
   - **User logon name**: jdoe
   - Click **Next**

5. Set a strong password:
   - Uncheck **User must change password at next logon** (optional)
   - Check **Password never expires** for lab use
   - Click **Next > Finish**

   📸 *Insert screenshot of completed new user wizard.*

---

## Step 6: Log In as Domain User

1. On the **Windows 11 Client VM**, sign out or restart the system.

2. On the login screen, click **Other user**.

3. Enter the new domain credentials:
   - **Username**: `yourdomain\jdoe`
   - **Password**: *(set in Step 5)*

   📸 *Insert screenshot of login using `jdoe` account.*

4. You should now be logged in as the new domain user.

---

## Notes

💡 If you're unable to join the domain, double-check:
- DNS points to the domain controller
- Firewall settings on the server
- That the client and server are on the same internal network

✅ Joining a Windows 11 machine to a domain simulates a common enterprise setup and enables you to practice user management, group policies, and permissions.

---

📸 *Insert screenshot suggestions where marked to enhance visual learning.*
