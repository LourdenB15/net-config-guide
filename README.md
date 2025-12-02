# Network Configuration Guide - Enhanced

## Equipment Setup Overview
- **Router**: Primary network device
- **Switch**: Network expansion device
- **Server Computer**: Static IP assignment
- **PC 1**: DHCP client with wireless capability

---

## Phase 1: Router Initial Setup

### 1.1 Hardware Reset
- Restart/power cycle the router
- Connect LAN cable from router LAN port to PC

### 1.2 Access Router Configuration
1. Press **Windows + R** to open Run dialog
2. Type `cmd` and press Enter
3. In Command Prompt, type: `ipconfig`
4. Note the **Default Gateway** address (typically 192.168.0.1 or 192.168.1.1)

### 1.3 Router Web Interface
1. Open web browser
2. Enter the Default Gateway IP address in the address bar
3. Create a new **admin password** (store securely)
4. Proceed to setup

---

## Phase 2: DHCP Server Configuration

### 2.1 DHCP Settings
1. Navigate to **DHCP Server** settings
2. Click **Exit Setup** wizard
3. Click **Advanced** settings
4. Configure **IP Address Pool**:
   - **Starting IP**: 192.168.0.20
   - **Ending IP**: 192.168.0.254 (recommended)
   - **Subnet Mask**: 255.255.255.0
   - **Lease Time**: 24 hours (or as needed)
5. Save settings

---

## Phase 3: Switch Integration

### 3.1 Physical Connections
1. Connect LAN cable from **Router LAN port** → **Switch uplink/port 1**
2. Connect another LAN cable from **Switch port** → **Server Computer**
3. Ensure all connections show link lights

---

## Phase 4: Server Computer Static IP Configuration

### 4.1 Access Network Settings
1. Open **Control Panel**
2. Navigate to **Network and Internet** → **Network Connections**
3. Right-click on **Ethernet adapter** → **Properties**
4. Select **Internet Protocol Version 4 (TCP/IPv4)** → **Properties**

### 4.2 Configure Static IP
- **IP Address**: 192.168.0.10 (or any IP outside DHCP pool range)
- **Subnet Mask**: 255.255.255.0
- **Default Gateway**: 192.168.0.1 (router IP)
- **Preferred DNS**: 192.168.0.1 (or 8.8.8.8 for Google DNS)
- **Alternate DNS**: 8.8.4.4 (optional)

### 4.3 Apply Settings
1. Click **OK** to save
2. **Disable/Enable** the network adapter to refresh connection

---

## Phase 5: Network Connectivity Testing

### 5.1 Server Computer Verification
Open Command Prompt on Server Computer:

```cmd
ipconfig
```
- Verify static IP is correctly assigned

```cmd
ping [Router Gateway IP]
```
- Example: `ping 192.168.0.1`
- Should receive replies (0% packet loss)

```cmd
ping [PC 1 IP Address]
```
- Verify connectivity to other devices once they're online

---

## Phase 6: PC 1 Wireless Configuration

### 6.1 Wireless Network Setup
1. Access router wireless settings
2. Configure **SSID** (network name)
3. Set **Security Mode**: WPA2-PSK or WPA3-PSK
4. Create strong **Password** (min. 8 characters)
5. Save wireless settings

### 6.2 PC 1 Connection
1. On PC 1, click network icon in system tray
2. Select configured SSID
3. Enter password
4. Click **Connect**
5. Verify connection status

### 6.3 Connection Test
```cmd
ipconfig
ping 192.168.0.1
ping 192.168.0.10
```
- Verify DHCP assignment (IP should be in 192.168.0.20-254 range)
- Test router connectivity
- Test server connectivity

---

## Troubleshooting Quick Reference

| Issue | Solution |
|-------|----------|
| Can't access router | Check cable, verify default gateway IP |
| No DHCP assignment | Verify DHCP is enabled, restart router |
| Can't ping devices | Check firewall settings, verify subnet mask |
| Wireless not working | Verify SSID broadcast is enabled |
| Static IP conflict | Ensure IP is outside DHCP pool range |

---

## Network Summary
- **Router IP**: 192.168.0.1
- **Server IP**: 192.168.0.10 (Static)
- **DHCP Pool**: 192.168.0.20 - 192.168.0.254
- **Subnet Mask**: 255.255.255.0

**Setup Complete** ✓
