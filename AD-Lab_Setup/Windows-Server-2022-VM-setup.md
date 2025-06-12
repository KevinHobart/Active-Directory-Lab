
# Windows Server 2022 VM Setup
This guide provides step-by-step instructions for downloading, creating, and setting up a Windows Server 2022 VM using VirtualBox 7.0.

---

## Step 1: Download the Windows Server 2022 ISO

1. Visit the **Microsoft Evaluation Center Page** for [Windows Server 2022](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2022).
2. Under **Get started for free**, choose **Download the ISO** option.
   ![1ISO-dwnld](https://github.com/user-attachments/assets/ac4fe9cc-176e-4299-89a9-971c224ba04a)

3. Fill out the **Register for your free trial today** form, and then select **Download now**.
   ![2ISO-dwnld](https://github.com/user-attachments/assets/9056d2df-380f-471b-94b5-b0962cc3ef6e)

4. Choose the **64-bit edition** ISO in your preferred language. The ISO file will be large (around 5-6GB), so allow time for the download.
   ![3ISO-dwnld](https://github.com/user-attachments/assets/249a1db9-2395-4328-8818-e35000ba484d)


---

## Step 2: Creating the New Virtual Machine in VirtualBox

1. Open VirtualBox and select **New** to create a new virtual machine.

   - **Name**: Something like "Windows Server 2022" or "WS2022-Lab"
   - **Folder**: Leave as default unless you have a custom VM directory.
   - **ISO Image**: Browse to and select the downloaded Windows Server 2022 ISO.
   - Be sure to select **Skip Unattended Installation**.
   - Click **Next**
   ![4VBox-setup](https://github.com/user-attachments/assets/98b6e46b-038b-4bf0-a366-d5c14a12920f)


2. **Hardware Configuration**

   - **Base Memory**: Minimum 4GB; Recommended 8GB or more for better performance.
   - **Processors**: Minimum 2; Recommended 4.
   - Click **Next**  
   ![5VBox-setup](https://github.com/user-attachments/assets/3fbbb6a2-e2db-4b37-bccc-1b6ba5bd9bc4)

   
3. **Virtual Hard Disk**

   - Choose **Create a Virtual Hard Disk Now**
   - Default settings are fine: 50GB dynamically allocated (you can increase based on use case)
   - Click **Next**  
   ![6VBox-setup](https://github.com/user-attachments/assets/f5daf426-d0b4-4b6c-b3a8-c78870f5be13)


4. **Summary**

   - Double-check settings
   - Confirm that **Skip Unattended Install** is *true*
   - Click **Finish**  
   ![7VBox-setup](https://github.com/user-attachments/assets/7f0caf10-e14f-42ab-bec4-f181b8387286)


---

## Step 3: Powering on and Installing Windows Server 2022

1. Select the **Windows Server 2022 VM** and click the green **Start** arrow to boot.

2. Windows Server 2022 Setup

   - Select **Language**, **Time and Currency Format**, and **Keyboard**. Leave defaults unless needed.
   - Click **Next**
   ![8install](https://github.com/user-attachments/assets/12880674-3c7e-4eb7-83c0-f1fab0c4f733)


   - Click **Install now**
   ![9install](https://github.com/user-attachments/assets/5345e1e1-cbef-4b3d-848a-3f67e068ff0b)


3. Select Operating System Edition

   - Choose **Windows Server 2022 Standard Evaluation (Desktop Experience)** so it installs with a GUI (important!).
   - Click **Next**
   ![10install](https://github.com/user-attachments/assets/53296080-bd7f-4892-a37b-33cf887876f0)


4. Accept the license terms and click **Next**
   ![11install](https://github.com/user-attachments/assets/65392e75-8860-4cf6-9dff-bb12ad381412)


5. Choose **Custom: Install Windows only (advanced)**

   - Select the virtual hard drive and click **Next**
   ![12install](https://github.com/user-attachments/assets/755b22fa-eac7-4f82-b6f7-b04dddc5ed9f)


6. Installation will begin. This may take several minutes. Windows will restart multiple times.

---

## Step 4: Final Setup and Admin Account Creation

1. On first boot, you’ll be prompted to set a password for the built-in **Administrator** account.

   - Enter and confirm a strong password.
   ![13pswd](https://github.com/user-attachments/assets/cd6f0f21-599f-41ce-ab4a-757b31d63558)


2. Press **Ctrl+Alt+Del** to log in, then enter the password you just set.
   ![15login](https://github.com/user-attachments/assets/985e0ec1-0c03-4953-b265-6f57f568ad05)


---

## Step 5: Install Guest Additions and Take a Snapshot

1. Log in to your **Windows Server 2022** VM.

2. Go to the **Devices** menu in the VirtualBox window and choose **Insert Guest Additions CD image…**
   ![16guest](https://github.com/user-attachments/assets/8cc2ed15-50c7-4e12-9009-798505d634c4)


3. If Autorun doesn't trigger:
   - Open **File Explorer**
   - Navigate to **CD Drive**
   - Right-click **VBoxWindowsAdditions-amd64.exe** and choose **Run as administrator**
   ![18guest](https://github.com/user-attachments/assets/3adf7989-f095-416f-8521-f771d54f333b)
   ![19guest](https://github.com/user-attachments/assets/0d7b2f89-cbf9-4bd3-a3ce-1e4b39d0924e)


4. Follow the Guest Additions setup wizard. Keep all defaults.
   ![20guest](https://github.com/user-attachments/assets/25ea1a08-1b22-4a87-9312-7530fbd38a57)


5. Once finished, reboot the VM.

6. Log back in after reboot.

7. **Take a Snapshot** of the clean install:

   - In VirtualBox, go to **Machine > Take Snapshot**
   - Name it something like `WS2022-CleanInstall`
   ![22snap](https://github.com/user-attachments/assets/8741e08f-7438-4dce-b732-660cae2a7f60)


---

## Notes

- **Windows Server Evaluation** is valid for 180 days. It can be rearmed a few times for testing purposes.
- This setup is ideal for practicing Active Directory, DNS, DHCP, or Windows Server roles.
