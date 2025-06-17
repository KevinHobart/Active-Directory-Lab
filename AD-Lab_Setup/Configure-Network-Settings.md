
# Configure Network Settings for Windows Server (Domain Controller) and Windows 11 (Client)

This guide helps you configure network settings for a Windows Server 2022 VM (already set up as a Domain Controller) and prepare for a Windows 11 client to join the domain.  
This Configuration must be done **Before** joining the Windows 11 client to the domain.  
**NOTE:**  I am including **two** options for network configurations.  
- The first will be a simple, more straight-forward network configuration utilizing a *NAT Network* in which both VMs can access the internet and can interact with the host machine.  This will work great for initial setup and performing various administration-type labs.  
- The second network configuration will more closely resemble a network found in a real-world enterprise setting.  The server (Domain Controller) will have access to the internet, and will route traffic from the Internal Network (Client machines) to the NAT adapter to provide internet access for the Windows 11 VM (Client). This option is a more in-depth setup, but is a more realistic example of how a network might look in an enterprise setting.
  
I would recommend that the initial network configuration be *NAT Network*.  I will put the *NAT Network* configuration tutorial first, followed by the *Internal Network* configuration tutorial.  
This is a lengthy tutorial, so I won't include screenshots for every step, but I'll try to include them when I think it might be helpful.  

---

## Step 1: Set the VirtualBox Network Adapter Type

You’ll need to configure two network adapters for your **Windows Server 2022** VM:

- **Adapter 1** (Internal network for domain traffic)
- **Adapter 2** (NAT or Bridged for internet access, optional)

### 1. Power off the Windows Server 2022 VM if it is running.

### 2. In VirtualBox:
- Right-click your **Windows Server 2022 VM** and choose **Settings**
- Go to the **Network** tab
- **Adapter 1**:
  - Check **Enable Network Adapter**
  - Attached to: **Internal Network**
  - Name: `LabNet` *(you can choose any consistent name)*
  - Click **Advanced** → Ensure **Adapter Type** is **Intel PRO/1000 MT Desktop (82540EM)**
  - Promiscuous Mode: **Allow All**

  📸 _Screenshot here: VirtualBox network settings showing Adapter 1 configured for Internal Network_

- **Adapter 2** *(optional, for internet access)*:
  - Check **Enable Network Adapter**
  - Attached to: **NAT** or **Bridged Adapter** (depending on your host setup)
  - Keep default settings

  📸 _Screenshot here: Adapter 2 configured for NAT or Bridged Adapter_

- Click **OK** to save settings

---

## Step 2: Configure the Server's IP Address

### 1. Start the Windows Server 2022 VM

### 2. Log in using the **Administrator** account

### 3. Open **Network Connections**:
- Right-click the Start Menu → **Network Connections**
- Click **Change adapter options**

  📸 _Screenshot here: Network Connections window showing multiple adapters_

### 4. Identify the correct adapter (Internal Network)
- It will usually not have internet access
- You can rename it to something like `LAN - Internal`

### 5. Set Static IP:
- Right-click the Internal adapter → **Properties**
- Select **Internet Protocol Version 4 (TCP/IPv4)** → **Properties**
- Enter the following:

```
IP address:     192.168.100.10
Subnet mask:    255.255.255.0
Default gateway: Leave blank or set to 192.168.100.1 (if routing)
Preferred DNS:  192.168.100.10
```

  📸 _Screenshot here: IPv4 settings dialog with static IP entered_

- Click **OK**, then **Close**

---

## Step 3: Verify DNS Role is Installed and Running

### 1. Open **Server Manager**
- Click **Tools > DNS**

### 2. Confirm the DNS role is running:
- Your domain should appear under **Forward Lookup Zones**
- The server’s hostname and records should already exist

  📸 _Screenshot here: DNS Manager showing domain and forward lookup zones_

---

## Step 4: Test Server Connectivity

### 1. Open **Command Prompt** as Administrator

### 2. Run the following:
```
ipconfig /all
ping 192.168.100.10
nslookup yourdomain.local
```

- Ensure the static IP shows up correctly
- `ping` should respond from the server’s IP
- `nslookup` should return the Domain Controller as the DNS server

  📸 _Screenshot here: Command prompt output from `ipconfig` and `nslookup`_

---

## Step 5: Prepare the Windows 11 Client

You’ll configure the **Windows 11 client VM** to use the same Internal Network as the server and manually set its DNS server to the Domain Controller's IP.

### 1. Configure VirtualBox Network Adapters for the Windows 11 VM

- Power off the **Windows 11 VM**
- In VirtualBox, right-click the VM → **Settings**
- Go to the **Network** tab

#### **Adapter 1**:
- Check **Enable Network Adapter**
- Attached to: **Internal Network**
- Name: `LabNet` (must match the Server's network name)
- Adapter Type: **Intel PRO/1000 MT Desktop (82540EM)**
- Promiscuous Mode: **Allow All**

📸 _Screenshot here: Adapter 1 for Windows 11 set to Internal Network_

#### **Adapter 2 (optional)**:
- Attached to: NAT or Bridged (optional for internet)

📸 _Screenshot here: Optional Adapter 2 for internet access_

Click **OK** to save and close settings.

### 2. Start the Windows 11 VM and Log In

- Use the local account you set up during install.

### 3. Open Network Settings

- Go to **Settings > Network & Internet > Ethernet**
- Click on the Ethernet connection (should be labeled something like “Network”)
- Scroll down and click **Edit** under **IP assignment**
- Change setting from **Automatic (DHCP)** to **Manual**

📸 _Screenshot here: IP assignment section in Windows 11 network settings_

### 4. Enable IPv4 and Enter the Following:

```
IP address:     192.168.100.20
Subnet prefix length: 24
Gateway:        Leave blank or use 192.168.100.1
Preferred DNS:  192.168.100.10
Alternate DNS:  Leave blank or set to a public DNS temporarily
```

📸 _Screenshot here: Manual IPv4 entry for Windows 11 client_

Click **Save** when done.

### 5. Test DNS Resolution to the Domain Controller

1. Open **Command Prompt** as Administrator

2. Run the following:

```
ipconfig /all
ping 192.168.100.10
nslookup yourdomain.local
```

📸 _Screenshot here: Windows 11 command prompt showing `ipconfig`, `ping`, and `nslookup`_

### 6. Take a Snapshot (Optional)

Now is a great time to take a **VirtualBox snapshot** of the Windows 11 client in a clean state before joining the domain.

---

## Notes

- Ensure both VMs use the **same Internal Network name** (`LabNet`)
- Avoid IP conflicts; assign static IPs outside of any DHCP scope
- You can optionally install a routing or NAT tool on the server if internet is needed for clients










## Step 1: Set a Static IP Address

1. Open **Settings** > **Network & Internet** > **Ethernet** > **Change Adapter Options**

2. Right-click your Ethernet adapter > **Properties**  
3. Select **Internet Protocol Version 4 (TCP/IPv4)** > **Properties**

4. Choose **Use the following IP address** and enter:
   - **IP address**: `192.168.1.10` (example)
   - **Subnet mask**: `255.255.255.0`
   - **Default gateway**: `192.168.1.1`
   - **Preferred DNS**: `127.0.0.1`
   - **Alternate DNS**: leave blank or use `8.8.8.8`

   **📷 Screenshot placeholder**
