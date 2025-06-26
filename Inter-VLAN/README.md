# 👨‍💼 Understanding Inter-VLAN Routing

## 📄 What is Inter-VLAN Routing?

**Inter-VLAN routing** allows communication between different VLANs (Virtual Local Area Networks) in a network. Since VLANs segment a network for better performance and security, a router or Layer 3 switch is needed to forward traffic between them.

Without inter-VLAN routing, devices in different VLANs cannot communicate with each other.

---

## 💡 Why Use Inter-VLAN Routing?

- 📈 Enable communication across multiple VLANs
- 🛡️ Maintain segmentation and security
- 🧰 Improve network management and traffic control
- 🌐 Enable centralized services (like DHCP, servers) across VLANs

---

## 🛠️ How Inter-VLAN Routing Works

There are two main methods:

### 1. Router-on-a-Stick (Using a Router)

- A single physical router interface is configured with multiple sub-interfaces.
- Each sub-interface is assigned to a VLAN.

## Project Explanation:

**Switch0 Configuration:**

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
no shutdown
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

**Switch1 Configuration:**

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
no shutdown
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
ip address 192.17.99.3 255.255.255.0
no shutdown
interface range fa0-2/1
switchport mode trunk
switchport trunk native vlan 99
no shutdown
```

**Router0 Configuration:**

```bash
interface fa0/0
no shutdown
interface fa0/0.10
encapsulation dot1Q 10
ip address 192.17.10.1 255.255.255.0
no shutdown
interface fa0/0.20
encapsulation dot1Q 20
ip address 192.17.20.1 255.255.255.0
no shutdown
interface fa0/0.30
encapsulation dot1Q 30
ip address 192.17.30.1 255.255.255.0
no shutdown
```

---

## 🔍 Practical Scenario

**Network Layout:**

```
PC0 (VLAN 10) --- Switch0 --- Switch2 --- Router --- Switch2 --- Switch1 --- PC4 (VLAN 20)
```

- Without Inter-VLAN routing: No communication between different VLAN occur
- With Inter-VLAN routing: PC0 can ping PC4 and vice-versa.

---

## 👥 Advantages and Disadvantages

|                 Advantages                  |                    Disadvantages                     |
| :-----------------------------------------: | :--------------------------------------------------: |
|    Efficient communication across VLANs     |            Slight increase in complexity             |
|       Centralized routing management        | Possible bottleneck if using single-router interface |
| Reduces need for multiple physical networks |                                                      |

---

## 🛠️ Troubleshooting Inter-VLAN Routing

- Ensure correct VLAN assignments on switch ports.
- Verify trunk links between switches and router/switch.
- Check IP addressing and gateway configurations.
- Confirm that interfaces and VLANs are active ("no shutdown").

---

## 🔗 Additional Resources

- [Cisco Inter-VLAN Routing Guide](https://www.cisco.com/c/en/us/td/docs/switches/lan/campus_lan_solutions/InterVLAN.html)
- [Networking Academy VLAN and Inter-VLAN Routing Course](https://www.netacad.com/)

---
