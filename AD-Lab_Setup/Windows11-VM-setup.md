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
     ![PressAnyKey](https://github.com/user-attachments/assets/30858b05-253b-430e-b9f2-ca3787fc4c90)

2. Installion of Windows 11 (Windows Setup).

   - Select **Language to install** and  **Time and Currency format**.  Leave as default for English.
   - Select **Next**
     ![VM_setup1](https://github.com/user-attachments/assets/732a48db-7083-4dc5-833d-0ae0f3db183a)

   - Select **Keyboard or input method**  Leave as default for US.
   - Select **Next**
     ![VM-setup2](https://github.com/user-attachments/assets/62e717c2-1175-4e34-b8d0-9455ee923f67)

   - Select **Install Windows 11**, select the **I agree...** box.  NOTE: Windows might reboot a few times during the installation process.  This is normal, and it should pick up where it left off.
   - Select **Next**
     ![VM-setup3](https://github.com/user-attachments/assets/cd3d2c2a-8ebb-4ed2-9327-ffa44ccb8695)

   - Accept the **Applicable notices and License Terms**
   - Select **Accept**  
     ![license-terms](https://github.com/user-attachments/assets/cb812eb6-d0f6-48db-a382-76d83a250483)

   - **Select location to install Windows 11**
   - Use Defaults and Select **Next**.
     ![VM-setup4](https://github.com/user-attachments/assets/6713106e-a466-49e3-9eb7-f5a5c9a0a087)

   - Select **Install**
     ![VM-setup5](https://github.com/user-attachments/assets/0c7fc096-efb5-4b1d-9c8f-d8bf0f9d6b8b)


---

## Step 4: Continue final setup and create user account for Windows 11 VM

1. Select the right region, followed by the right keyboard layout. Select **Skip** for second keyboard layout.
   ![VM-setup6](https://github.com/user-attachments/assets/9ae23005-e112-4c94-8ea3-6fffc3aa33d7)
   ![VM-setup7](https://github.com/user-attachments/assets/e11bb6f8-e25b-4882-b1b1-ff6629f61042)
   ![VM-setup8](https://github.com/user-attachments/assets/642368eb-d04f-47ee-bcc1-7c7d78dfa33e)



3. Create User Account
   - -**Important**-
   - Select **Sign in options**
     ![W11-user-acct1](https://github.com/user-attachments/assets/4c12e394-aff6-4541-a3b9-b0e1bfc33f80)

   - Select **Domain join instead**.  This will allow you to join this computer (Windows 11 VM) to the Active Directory Domain Controller.
     ![VM-user-acct2](https://github.com/user-attachments/assets/5a84c26a-799c-49a9-9c48-08fb59b65925)

   - Enter a name.
     ![VM-user-acct3](https://github.com/user-attachments/assets/5628e16e-12a1-4b4a-8f68-4105b20b5f81)

   - Enter and Confirm your password.
     ![VM-user-acct4](https://github.com/user-attachments/assets/1563232f-d1fa-41ed-a4c4-21ce26cb454e)

   - Add your security questions (3).
     ![VM-user-acct6](https://github.com/user-attachments/assets/cca6c846-08ae-4155-83fc-4095e2468116)

4. Choose privacy settings for your device.
   - Adjust these to your preference
   - Select **Accept**
     ![VM-user-acct7](https://github.com/user-attachments/assets/2c4c8b4d-552d-4fa7-91d9-1455fa9e2961)

5. Windows will now update if necessary (this could take some time).  Once Windows 11 is done updating, it will restart and you will presented with the login screen.
   ![VM-user-acct8](https://github.com/user-attachments/assets/8a792ca5-7718-4e06-aa23-6789ebf569eb)

---

## Step 5: Install Guest Tools onto the virtual machine

1. Log in to Windows 11
   ![VM-final1](https://github.com/user-attachments/assets/73ee0f45-ceb6-46a7-8539-aea4e26a7093)

3. Go to **Devices** and then select **Insert Guest Additions CD image...**
   ![VM-final2](https://github.com/user-attachments/assets/69a6730a-1728-48df-8d48-d268212a0bdb)

5. If Autorun doesn't work:
   - Go to **File Explorer**
     ![Guest-add1](https://github.com/user-attachments/assets/456be18c-e22c-47fa-86cc-18cf16b50c72)

   - Select **CD Drive**
     ![VM-Guestadd2](https://github.com/user-attachments/assets/3164d358-e48e-4a92-b36d-e0c4cd5c596d)

   - Right Click on **VBoxWindowsAdditions-amd64** and run as administrator.
     ![VM-guestadd3](https://github.com/user-attachments/assets/3ffb3403-56ba-46cc-a01a-0e4c698ecb30)

   - Select **Next** to start Setup.  Stay with defaults on all.
     ![VM-guest4](https://github.com/user-attachments/assets/038e4274-56fd-445e-8f18-c38a9a3647b2)

   - When finished, Select **Reboot now**, then select **finish**. If this screen is not visible, it might be behind the File Explorer page. You can close the File Explorer, if needed.
     ![VM-guest5](https://github.com/user-attachments/assets/887c88ab-5c29-46bd-865b-dcbb4f1f0fb1)

6. Once Windows 11 reboots, you can log in as the user you created.
   ![VM-guest6](https://github.com/user-attachments/assets/ba139196-95fc-4392-8a34-bd06273389e4)

   

