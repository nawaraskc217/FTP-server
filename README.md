# 🖥️ FTP Server Setup on Windows (Local Network)

This guide explains how to create and access an FTP server on a Windows PC (e.g., MGhost) from another device (e.g., Nawaras-PC) over a local network.

---

## ✅ Prerequisites

- A Windows PC that will act as the **FTP server**
- Other PC(s) connected to the **same local network**
- Administrator privileges on the FTP host

---

## ⚙️ Step-by-Step Instructions

### 1. Install FTP Server Feature

1. Go to **Control Panel > Programs > Turn Windows features on or off**
2. Expand **Internet Information Services**
3. Check:
   - **FTP Server**
     - ✅ FTP Service
     - ✅ FTP Extensibility
   - **Web Management Tools**
     - ✅ IIS Management Console
4. Click **OK** and let it install.

---

### 2. Create FTP Shared Folder

1. Create a folder, e.g., `C:\FTPShared`
2. Right-click the folder > **Properties** > **Sharing** tab
3. Click **Share...**
4. Share with **Everyone**
5. Click **Permissions** and allow **Read/Write** access if needed

---

### 3. Configure FTP Site in IIS

1. Open **IIS Manager** (search for "IIS" in the Start menu)
2. In the left pane, expand your PC name
3. Right-click **Sites** > **Add FTP Site**
4. Name it `MyFTP` (or any name) and set the physical path to `C:\FTPShared`
5. Click **Next**
   - IP Address: choose your local IP
   - Port: **21**
   - Enable: ✅ **Start FTP site automatically**
6. Click **Next**
   - Authentication: ✅ **Basic**
   - Authorization:
     - Access to: **Specified users** or **Everyone**
     - Permissions: ✅ **Read**, ✅ **Write**

---

### 4. Allow FTP Through Windows Firewall

1. Go to **Windows Defender Firewall**
2. Click **Allow an app or feature through Windows Defender Firewall**
3. Ensure **FTP Server** and **IIS** are allowed for **Private** networks

**OR** (manually):

1. Open **Windows Defender Firewall > Advanced Settings**
2. Go to **Inbound Rules**
3. Add rules to allow TCP ports:
   - **21** (FTP command)
   - **20** (FTP data)

---

### 5. Access the FTP Server from Another PC

From another PC on the same network:

1. Open **File Explorer**
2. In the address bar, type: ``ftp://192.168.0.10:21 `` or 
    1. add network a network location

3. Press Enter
4. Log in using your Windows username/password if prompted

---

### ✅ Optional: Map FTP as Network Drive

1. Right-click **This PC** > **Map network drive**
2. In Folder field, enter:




# Extra IDEA

3. Check ✅ **Reconnect at logon**
4. Click **Finish**

---

## 🧪 Example IP Setup

| Device       | IP Address      | Connection         |
|--------------|------------------|---------------------|
| MGhost       | 192.168.0.10     | Main Router (LAN)   |
| Nawaras-PC   | 192.168.0.11     | Secondary Router LAN (bridged) |
| Router       | 192.168.0.1      | Gateway             |

---

## 🚫 Troubleshooting

- Make sure both PCs are on the **same subnet** (e.g., `192.168.0.x`)
- Check that **port 21** is open in the firewall
- If you can't connect, try disabling the Windows firewall temporarily (for testing only)

---

## 🌐 Want FTP Access from the Internet?

You'll need to:
- Set a **static IP** for the FTP host
- Configure **port forwarding** on your router
- Use a **dynamic DNS** service (optional)

Let me know if you want this setup too.

---

### 📁 You're now ready to transfer files over FTP!

