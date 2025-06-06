# Windows 11 VM Setup
This guide will provide instructions on how to download, create and set up a Windows 11 VM (Virtual Machine) using VirtualBox 7.0.

---

## Step 1: Download the Windows 11 ISO
1. Visit the **Microsoft Evaluation Center Page** for [Windows 11 Enterprise](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-11-enterprise).
2. Under **Get started for free**, Select the ISO for Windows 11 Enterprise.
   ![Windows-ISO](https://github.com/user-attachments/assets/615dc9dd-e5bf-47d8-8183-26eadf9d12df)
3. Fill out the **Register for your free trial today** form, and select **Download now**.(see screenshot).
   ![Windows-ISO-Register-Form](https://github.com/user-attachments/assets/e820aed7-cf49-4ee9-bfc9-515f1259ef1d)
4. Select the 64-bit edition of the ISO - Enterprise download in the language preferred.  The file is over 5GB, so it may take some time to download.  The file can be saved to your Downloads folder, or whatever folder you prefer.
   ![64-bit-iso](https://github.com/user-attachments/assets/2d52c3f8-e102-4845-ae43-f7cb56715d46)

---

## Step 2: Creating the new virtual machine in VirtualBox
1. Open VirtualBox and select **New** to add a new virtual machine.

   - Name: Name the virtual machine.  Example:  Windows 11, Windows 11 Lab, Windows 11 AD Lab.
   - Folder: Leave as default unless you have a specific folder you would like the VM files to be stored in.
   - ISO Image: Select the location of the ISO you downloaded.
   - Be sure to select **Skip Unatteneded Installation**.
   - Select **Next**
    ![VB1](https://github.com/user-attachments/assets/bde219a6-778c-46e0-bc01-800540ec519e)
2. **Hardware**  This is where you will designate hardware resources to the VM.  It is best to keep the slider in the green area.

   - Base Memory: 4GB Minimum, 8GB Recommended.
   - Processors: 2 Minimum, 4 Recommended.
   - Select **Next**
   ![VM-Hardware](https://github.com/user-attachments/assets/5aac47d3-4e29-41b1-b53c-c1598cedfa38)
3. **Virtual Hard disk**

   - Select **Create a Virtual Hard Disk Now**.
   - Leave all else as default.
   - Select **Next**
   ![VM-HD](https://github.com/user-attachments/assets/e1c91087-1614-4a97-8b1c-ccda854c2b49)
4. **Summary**

   - This shows a summary of the configurations you have chosen for the VM.
   - Ensure that **Skip Unattended Instal** is *true*.
   - Select **Finish**
   ![VM-Summary](https://github.com/user-attachments/assets/09b5c35a-3b43-4275-99b2-ce61377f391e)

---

## Step 3: Powering on and Installing Windows 11 on the virtual machine
1. Powering on Windows 11 VM for the first time.

   - Select **Windows 11** VM, then Select the green **Start** arrow.
   ![VM-Start](https://github.com/user-attachments/assets/9e4e144f-5bfb-448f-bac4-9ec50aff4b1a)

   - Click inside of the newly opened window.  It will display **Press any key to boot from CD or DVD..**  Press any key to continue.

2. Installion of Windows 11 (Windows Setup).

   - Select **Language to install** and  **Time and Currency format**.  Leave as default for English.
   - Select **Next**
     ![VM_setup1](https://github.com/user-attachments/assets/732a48db-7083-4dc5-833d-0ae0f3db183a)

   - Select **Keyboard or input method**  Leave as default for US.
   - Select **Next**
     ![VM-setup2](https://github.com/user-attachments/assets/62e717c2-1175-4e34-b8d0-9455ee923f67)

   - Select **Install Windows 11**, select the **I agree...** box.  NOTE: Windows might reboot a few times during the installation process.  This is normal, and it should pick up where it left off.
   - Select **Next**
   - Accept the **Applicable notices and License Terms**
   - Select **Accept**
   - **Select location to install Windows 11**
   - Use Defaults and Select **Next**.
   - Select **Install**

---

## Step 4: Continue final setup and create user account for Windows 11 VM

1. Select the right region, followed by the right keyboard layout. Select **Skip** for second keyboard layout.
2. Create User Account
   - -**Important**-
   - Select **Sign in options**
   - Select **Domain join instead**  This will allow you to join this computer (Windows 11 VM) to the Active Directory Domain Controller.
   - Enter a name.
   - Enter and Confirm your password.
   - Add your security questions (3).
3. Choose privacy settings for your device.

   - Adjust these to your preference
   - Select **Accept**
4. Windows will now update, if necessary (this could take some time).  Once Windows 11 is done updating, it will restart and you will presented with the login screen.

## Step 5: Install Guest Tools onto the virtual machine

1. Log in to Windows 11
2. Go to **Devices** and then select **Insert Guest Additions CD image...**
3. If Autorun doesn't work:
   - Go to **File Explorer**
   - Select **CD Drive**
   - Right Click on **VBoxWindowsAdditions-amd64** and run as administrator.
   - Select **Next** to start Setup.  Stay with defaults on all.
   - When finished, Select **Reboot now**, then select **finish**  If this screen is not visible, it might be behind the File Explorer page. You can close the File Explorer, if needed.
4. Once Windows 11 reboots, you can log in as the user you created.
   

