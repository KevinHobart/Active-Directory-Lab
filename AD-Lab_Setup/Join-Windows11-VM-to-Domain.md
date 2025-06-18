# Join Windows 11 VM to the Domain & Create a Domain User

This tutorial will be the final tutorial for setting up an Active Directory home lab. It will provide steps on how to join a Windows 11 VM to your Active Directory domain, and then how to create a new domain user for login. Ensure both your **Windows Server 2022 Domain Controller** and **Windows 11 Client** are powered on, connected to the same network, and properly configured.

---

## Step 1: Verify Network Connectivity

1. On the **Windows 11 Client VM**, open **Command Prompt** and ping the domain controller.

   ```bash
   ping dc01.local
   ```

   Replace `dc01.local` with your actual domain name.

   - If the ping is successful, proceed.
   - If not, check your network settings and DNS configuration.

   📸 *Insert screenshot of a successful ping from Windows 11 to the DC.*

---

## Step 2: Rename the Windows 11 PC
Before joining the Windows 11 VM to the domain, you'll want to rename the PC so it is easily identifiable when viewed on the domain controller.  A good naming convention would be **WS01**.  This denotes it as Workstation 01.  In the future, you can add more machines and continue with the naming scheme - WS02, WS03....WS21, and so on.
1. On the **Windows 11 Client VM**:
   - Open **Settings > System > About**
   - Click **Rename this PC**

   📸 *Insert screenshot of the "About" page with the rename link.*

2. Enter the new name: `WS01`

3. Click **Next**, then **Restart now** when prompted.

   📸 *Insert screenshot of confirmation to rename and restart.*

4. After restart, verify the name change by opening **Command Prompt** and typing:

   ```bash
   hostname
   ```

   It should return `WS01`.

---

## Step 3: Join Windows 11 to the Domain

1. On the **Windows 11 Client VM**:
   - Open **Settings > System > About**
   - Click **Domain or workgroup** under **Related links**.

   📸 *Insert screenshot of the "About" page with the domain link.*

2. In the **System Properties** window, click **Change**.

   📸 *Insert screenshot of the Computer Name/Domain Changes window.*

3. Under **Member of**, select **Domain**, and enter your domain name (e.g., `dc01.local`).

4. Click **OK**.

5. Enter credentials for a domain user with permission to join the domain (usually the domain admin):
   - **Username**: `Administrator`
   - **Password**: *(your domain admin password)*

6. If successful, you’ll get a welcome message to the domain. Click **OK**.

   📸 *Insert screenshot of successful domain join message.*

7. You will be prompted to restart. Click **OK** and then restart the VM.

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
