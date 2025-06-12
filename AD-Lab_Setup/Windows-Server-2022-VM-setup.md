
# Windows Server 2022 VM Setup
This guide provides step-by-step instructions for downloading, creating, and setting up a Windows Server 2022 VM using VirtualBox 7.0.

---

## Step 1: Download the Windows Server 2022 ISO

1. Visit the **Microsoft Evaluation Center Page** for [Windows Server 2022](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2022).
2. Under **Get started for free**, choose **Download the ISO** option.
   > 📸 1
3. Fill out the **Register for your free trial today** form, and then select **Download now**.
   > 📸 2
4. Choose the **64-bit edition** in your preferred language. The ISO file will be large (around 5-6GB), so allow time for the download.
   > 📸 3

---

## Step 2: Creating the New Virtual Machine in VirtualBox

1. Open VirtualBox and select **New** to create a new virtual machine.

   - **Name**: Something like "Windows Server 2022" or "WS2022-Lab"
   - **Folder**: Leave as default unless you have a custom VM directory.
   - **ISO Image**: Browse to and select the downloaded Windows Server 2022 ISO.
   - Be sure to select **Skip Unattended Installation**.
   - Click **Next**
   > 📸 4

2. **Hardware Configuration**

   - **Base Memory**: Minimum 4GB; Recommended 8GB or more for better performance.
   - **Processors**: Minimum 2; Recommended 4.
   - Click **Next**
   > 📸 5
   
3. **Virtual Hard Disk**

   - Choose **Create a Virtual Hard Disk Now**
   - Default settings are fine: 50GB dynamically allocated (you can increase based on use case)
   - Click **Next**
   > 📸 6

4. **Summary**

   - Double-check settings
   - Confirm that **Skip Unattended Install** is *true*
   - Click **Finish**
   > 📸 7

---

## Step 3: Powering on and Installing Windows Server 2022

1. Select the **Windows Server 2022 VM** and click the green **Start** arrow to boot.

   - A window will appear with **Press any key to boot from CD or DVD...**
   - Click inside the window and press any key.
   > 📸 *Insert screenshot of "Press any key" prompt*

2. Windows Server 2022 Setup

   - Select **Language**, **Time and Currency Format**, and **Keyboard**. Leave defaults unless needed.
   - Click **Next**
   > 📸 *Insert screenshot of regional settings*

   - Click **Install Now**
   > 📸 *Insert screenshot of Install Now screen*

3. Select Operating System Edition

   - Choose **Windows Server 2022 Standard (Desktop Experience)** so it installs with a GUI (important!).
   - Click **Next**
   > 📸 *Insert screenshot showing OS edition options*

4. Accept the license terms and click **Next**
   > 📸 *Insert screenshot of license agreement*

5. Choose **Custom: Install Windows only (advanced)**

   - Select the virtual hard drive and click **Next**
   > 📸 *Insert screenshot of drive selection screen*

6. Installation will begin. This may take several minutes. Windows will restart multiple times.

   > 📸 *Insert screenshot of installation progress*

---

## Step 4: Final Setup and Admin Account Creation

1. On first boot, you’ll be prompted to set a password for the built-in **Administrator** account.

   - Enter and confirm a strong password.
   > 📸 *Insert screenshot of password setup*

2. Press **Ctrl+Alt+Del** to log in, then enter the password you just set.
   > 📸 *Insert screenshot of login screen*

---

## Step 5: Install Guest Additions and Take a Snapshot

1. Log in to your **Windows Server 2022** VM.

2. Go to the **Devices** menu in the VirtualBox window and choose **Insert Guest Additions CD image…**
   > 📸 *Insert screenshot of this VirtualBox menu option*

3. If Autorun doesn't trigger:
   - Open **File Explorer**
   - Navigate to **CD Drive**
   - Right-click **VBoxWindowsAdditions-amd64.exe** and choose **Run as administrator**
   > 📸 *Insert screenshot of VBox setup file and right-click context menu*

4. Follow the Guest Additions setup wizard. Keep all defaults.
   > 📸 *Insert screenshot of setup wizard*

5. Once finished, reboot the VM.

6. Log back in after reboot.

7. **Take a Snapshot** of the clean install:

   - In VirtualBox, go to **Machine > Take Snapshot**
   - Name it something like `WS2022-CleanInstall`
   > 📸 *Insert screenshot of snapshot dialog*

---

## Notes

- **Windows Server Evaluation** is valid for 180 days. It can be rearmed a few times for testing purposes.
- This setup is ideal for practicing Active Directory, DNS, DHCP, or Windows Server roles.
