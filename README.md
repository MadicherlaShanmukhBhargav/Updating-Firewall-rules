# FIREWALL RULES
## 📌 Objective  
Learn how to configure and test basic firewall rules on **Windows** and **Linux** to allow or block specific traffic.

## 🛡️ What is a Firewall?

A **firewall** is a security system that monitors and controls incoming and outgoing network traffic based on predefined rules.  
It is used to **protect systems from unauthorized access, block malicious traffic, and allow only trusted communication**.

## 🛠 Tools Used
- **Windows Firewall**  on Windows  
- **UFW (Uncomplicated Firewall)** on Linux  

## 🚀 Steps Performed
1. Setting up Firewall rules in Windows
2. Setting up the Firewall rules in Linux
3. Trying to take access to Windows over the SSH from Linux when SSH is open and close

## 📌 1. Setting up Firewall Rules in Windows

Windows uses **Windows Defender Firewall** to control inbound/outbound traffic.

### ✅ Steps via GUI:
1. Open **Windows Security** → Click on **Firewall & Network Protection**.
2. Select **Advanced Settings** → This opens **Windows Defender Firewall with Advanced Security**.
3. To create a new rule:
   - Click **Inbound Rules** → **New Rule**.
   - Choose **Port** → Select **TCP**.
   - Enter port number (e.g., `22` for SSH).
   - Select **Allow the connection** (to allow) or **Block the connection** (to block).
   - Name the rule (e.g., `Allow SSH`).
4. Repeat the same for **Outbound Rules** if required.

### NOTE:
- **Allow SSH** on port `22` → Remote systems can connect.  
- **Block SSH** on port `22` → Remote systems cannot connect.

# 

### ✅ Steps via Powershell:
1. Open powershell in Admin

---

## 📌 2. Setting up Firewall Rules in Linux

Linux commonly uses **ufw** (Uncomplicated Firewall) or **firewalld**. Below is with `ufw`.

### ✅ Steps (using ufw):
#### Check firewall status:
   ```bash
 sudo ufw status
   ```
#### Enable UFW (if disabled)
```bash
sudo ufw enable
```

#### Blocked Inbound Traffic on Port 23 (Telnet)
   ``` bash
   sudo ufw deny 23
   ```
Running sudo ufw deny 23/tcp → Linux will block Telnet connections.

####  Allowed Inbound Traffic on Port 22 (SSH)
``` bash
sudo ufw allow 22
```
Running sudo ufw allow 22/tcp → Linux will allow SSH connections.``

#### Listed Current Firewall Rules
   ```  bash
   sudo ufw status
   ```

#### Removed Test Rule to Restore Original State
``` bash
sudo ufw delete deny 22
```



---



#### Summarized Findings

- Firewall rules filter inbound and outbound traffic.

- Blocking insecure services to improves system security.

