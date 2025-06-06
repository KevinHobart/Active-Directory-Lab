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

## Step 2: Add the new virtual machine to VirtualBox
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

## Step 3: Powering on and Installing Windows 11
1. Powering on Windows 11 VM for the first time.

   - Select **Windows 11** VM, then Select the green **Start** arrow.
   - Click inside of the newly opened window.  It will display **Press any key to boot from CD or DVD..**  Press any key to continue.

2. Installion of Windows 11 (Windows Setup).

   - Select **Language**, **Time and Currency** and **Keyboard or input method**.  Leave as default for English.
   - Select **Next**
   - Select **Install now**  NOTE: Windows will reboot a few times during the installation process.  This is normal, and it should pick up where it left off.
   - Accept the **Microsoft Software License Terms**
   - Select **Next**
   - Select **Custom: Install Windows only (advanced)**.
   - Use Defaults and Select **Next**.  This will take a little bit and will probably restart a few times.

3. Installation of Windows 11 (con't)

   - 

