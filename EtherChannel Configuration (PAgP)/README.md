# 🛠️ PAgP (Port Aggregation Protocol) Configuration Guide

## 📄 What is PAgP?
**PAgP (Port Aggregation Protocol)** is a Cisco-proprietary protocol that automatically bundles multiple physical Ethernet links into a single logical link, known as an EtherChannel. This improves redundancy, increases bandwidth, and simplifies management.

PAgP helps switches negotiate the forming of an EtherChannel by exchanging packets between ports.

---

## 💡 Why Use PAgP?
- 🛡️ Enhances link redundancy and resiliency
- 📈 Increases available bandwidth between switches
- 🧰 Simplifies network management by treating multiple links as one logical connection
- 🔄 Automatic negotiation of EtherChannel

---

## 🛠️ Project Explanation: PAgP Configuration on Cisco Devices

**Switch0 Configuration:**:
```bash
interface range fa0/1,fa1/1,fa2/1
channel-group 1 mode desirable
exit
interface port-channel 1
switchport mode trunk
```

**Multilayer Switch0 Configuration:**:
```bash
interface range gig1/0/1-3
channel-group 1 mode auto
exit
interface port-channel 1
switchport mode trunk
interface range gig1/0/4-6
channel-group 2 mode desirable
exit
interface port-channel 2
switchport mode trunk
```

**Switch1 Configuration:**
```bash
interface range fa0/1,fa1/1,fa2/1
channel-group 2 mode auto
exit
interface port-channel 2
switchport mode trunk
```

> **Note:**
> - `desirable` actively tries to form an EtherChannel.
> - `auto` passively waits to respond to PAgP requests.

---

## 🔢 PAgP Modes
| Mode | Description |
|:----:|:-----------:|
| auto | Passively negotiates, responds to PAgP packets but does not initiate |
| desirable | Actively initiates and responds to PAgP packets |

---

## 🔗 Best Practices
- Always match speed and duplex settings across bundled ports.
- Ensure trunk/access mode consistency across ports.
- Use consistent VLAN configuration across the member ports.
- Use a dedicated EtherChannel for management traffic if needed.

---

## 🔍 Verification Commands
```bash
show etherchannel summary
show running-config interface port-channel 1
show interfaces port-channel 1
```
These commands help verify the health and status of EtherChannel and PAgP negotiation.

---

## 🛡️ Troubleshooting Tips
- Ports must have identical configurations (speed, duplex, mode, VLAN info).
- Ensure that "desirable" and "auto" modes are correctly set.
- Check that the physical links are up and error-free.

---

## 🔗 Additional Resources
- [Cisco PAgP Configuration Guide](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/lanswitch/configuration/xe-3s/lanswitch-xe-3s-book/lsw-pagp.html)
- [Cisco EtherChannel Overview](https://www.cisco.com/c/en/us/products/collateral/switches/campus-lan-switches-802-11ac/white-paper-c11-728216.html)

---