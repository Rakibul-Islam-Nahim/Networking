# 📚 VLANs (Virtual Local Area Networks)

## What is a VLAN?

A **VLAN** (Virtual Local Area Network) is a way to **logically separate** devices on the same physical network into different **virtual networks**.

Even if devices are connected to the same switch, **VLANs keep their traffic isolated** — just like they are on different physical switches!

> **In simple words:**  
> VLANs are like "invisible walls" inside a switch that separate computers into different groups.

---

## Why VLANs are Useful
- 🛡️ **Security:** Devices in different VLANs can't directly talk to each other without a router (Layer 3 device).
- 🏎️ **Performance:** Reduces unnecessary traffic (broadcast domains).
- 🔥 **Organization:** Group users by department, function, or project.
- 💰 **Cost-Efficient:** No need to buy separate physical switches for every group.

---

## Key Concepts

| Term | Explanation |
|:---|:---|
| **VLAN ID** | Each VLAN is identified by a unique number (1-4094). |
| **Access Port** | A switch port assigned to one VLAN. |
| **Trunk Port** | A port that carries traffic for **multiple VLANs** — typically between switches. |
| **Tagging** | VLAN information added into Ethernet frames using protocols like **802.1Q**. |
| **Native VLAN** | The VLAN that is sent **without tagging** on a trunk link (default is VLAN 1). |

---

## Project Explanation:

| Department | VLAN ID |
|:---|:---|
| HR | 10 |
| IT | 20 |
| Finance | 30 |

- HR PCs → VLAN 10  
- IT PCs → VLAN 20  
- Finance PCs → VLAN 30  
- Even if all connect to the same switch, they are isolated unless you allow routing between them.

---

## Configuration (Cisco CLI)

**Switch2 Configuration:**
```bash
vlan 10
name home
exit
vlan 20
name office
exit
vlan 30
name market
exit
vlan 99
name man
exit
interface vlan 99
ip address 192.17.99.1 255.255.255.0
interface fa0/1
switchport mode access
switchport access vlan 10
interface fa1/1
switchport mode access
switchport access vlan 20
interface fa2/1
switchport mode access
switchport access vlan 30
interface fa3/1
switchport mode trunk
switchport trunk native vlan 99
```
**Switch3 Configuration:**
```bash
vlan 10
name home
exit
vlan 20
name office
exit
vlan 30
name market
exit
vlan 99
name man
exit
interface vlan 99
ip address 192.17.99.3 255.255.255.0
interface fa0/1
switchport mode access
switchport access vlan 10
interface fa1/1
switchport mode access
switchport access vlan 20
interface fa2/1
switchport mode access
switchport access vlan 30
interface fa3/1
switchport mode trunk
switchport trunk native vlan 99
```

**Switch4 Configuration:**
```bash
vlan 10
name home
exit
vlan 20
name office
exit
vlan 30
name market
exit
vlan 99
name man
exit
interface vlan 99
ip address 192.17.99.2 255.255.255.0
interface fa2/1
switchport mode trunk
switchport trunk native vlan 99
interface fa3/1
switchport mode trunk
switchport trunk native vlan 99
```

## Configuration Details:
- Now The LAN is divided into three sub LAN 
- The Device under same VLAN and network ip can communicate with each other
- All though there is only one network connected with 3 switches but they will act like three different network. This is the concept of VLAN