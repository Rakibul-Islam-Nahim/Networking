# 🛠️ LACP (Link Aggregation Control Protocol) Configuration Guide

## 📄 What is LACP?
**LACP (Link Aggregation Control Protocol)** is an open-standard (IEEE 802.3ad) protocol used to automatically bundle multiple physical Ethernet links into a single logical link, called an EtherChannel. Unlike PAgP, LACP works across different vendor devices, providing greater interoperability.

LACP helps devices dynamically negotiate and maintain the aggregation of links.

---

## 💡 Why Use LACP?
- 🛡️ Improves network redundancy and load balancing
- 📈 Increases available bandwidth
- 🧰 Enables dynamic link management between multi-vendor devices
- 🔄 Provides automatic recovery if one link in the channel fails

---

## 🛠️ Project Explanation: LACP Configuration on Cisco Devices

**Switch0 Configuration:**:
```bash
interface range fa0/1,fa1/1,fa2/1
channel-group 1 mode active
exit
interface port-channel 1
switchport mode trunk
```

**Multilayer Switch0 Configuration:**:
```bash
interface range gig1/0/1-3
channel-group 1 mode passive
exit
interface port-channel 1
switchport mode trunk
interface range gig1/0/4-6
channel-group 2 mode active
exit
interface port-channel 2
switchport mode trunk
```

**Switch1 Configuration:**
```bash
interface range fa0/1,fa1/1,fa2/1
channel-group 2 mode active
exit
interface port-channel 2
switchport mode trunk
```

## 🔢 LACP Modes
| Mode | Description |
|:----:|:-----------:|
| active | Actively tries to form an EtherChannel by sending LACP packets |
| passive | Waits to respond to LACP packets but does not initiate |

---

## 🔗 Best Practices
- Ensure matching speed and duplex settings across member links.
- Use consistent trunk/access mode settings across aggregated ports.
- Maintain identical VLAN configurations across ports.
- Monitor the health of aggregated links for quick failure recovery.

---

## 🔍 Verification Commands
```bash
show etherchannel summary
show etherchannel port-channel
show lacp neighbor
```
These commands help confirm LACP negotiations and EtherChannel status.

---

## 🛡️ Troubleshooting Tips
- Verify matching configurations on both ends.
- Check for mismatched speed, duplex, or VLAN settings.
- Ensure that one side is set to active if the other is passive.
- Use `show lacp neighbor` to validate LACP partner information.

---

## 🔗 Additional Resources
- [Cisco LACP Configuration Guide](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/lanswitch/configuration/xe-3s/lanswitch-xe-3s-book/lsw-lacp.html)
- [IEEE 802.3ad Link Aggregation Standard](https://standards.ieee.org/standard/802_3ad-2000.html)

---
