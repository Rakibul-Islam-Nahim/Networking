# 📍 Native VLAN Configuration

## 📄 What is a Native VLAN?
A **Native VLAN** is the VLAN assigned to untagged traffic on a trunk port. In IEEE 802.1Q trunking, most VLAN traffic is tagged with a VLAN ID, but traffic without a VLAN tag is placed into the **native VLAN** by default.

By default, VLAN 1 is the native VLAN on Cisco devices, but it is considered best practice to change it for security reasons.

---

## 💡 Why Native VLAN Matters
- 🌐 Ensures proper communication with devices that send untagged traffic
- 🛡️ Helps maintain compatibility between devices from different vendors
- 🚫 Can be exploited if misconfigured — always set it intentionally

---

## 🛠️ Project Explanation: Native VLAN Configuration (Cisco IOS)
**Switch0 Configuration**
```bash
vlan 10
name home
exit
vlan 20
name office
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
interface fa3/1
switchport mode trunk
switchport trunk native vlan 99
```

**Switch1 configuration**
```bash
vlan 10
name home
exit
vlan 20
name office
exit
vlan 99
name man
exit
interface vlan 99
ip address 192.17.99.2 255.255.255.0
interface fa0/1
switchport mode access
switchport access vlan 10
interface fa1/1
switchport mode access
switchport access vlan 20
interface fa3/1
switchport mode trunk
switchport trunk native vlan 99
```

This sets VLAN 99 as the native VLAN on trunk port fa3/1. Any untagged traffic received on this interface will be associated with VLAN 99.

---

## 🔢 Key Points
- Untagged frames on a trunk port are assigned to the native VLAN.
- The native VLAN must match on both ends of a trunk link.
- Mismatched native VLANs can cause security vulnerabilities (e.g., VLAN hopping).

---

## 🔗 Best Practices
- 🚫 Avoid using VLAN 1 as the native VLAN.
- 🔒 Use a dedicated VLAN ID (not used for user traffic) as the native VLAN.
- ⚖️ Ensure consistent native VLAN configurations on both sides of trunk links.

---

## 🔍 Verification Commands
```bash
show interfaces trunk
show vlan brief
```
These commands will display the native VLAN settings and current VLANs on the switch.

---

## 🔗 Additional Resources
- [Cisco Native VLAN Guide](https://www.cisco.com/c/en/us/support/docs/lan-switching/8021q/10023-3.html)
- [Networking Academy VLAN Module](https://www.netacad.com/)

---
