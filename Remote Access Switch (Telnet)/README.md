# 📼 Telnet Configuration Guide

## 📄 What is Telnet?
**Telnet** (short for *Teletype Network*) is a protocol used to remotely access and manage devices over a network using a command-line interface. Though considered outdated and insecure compared to SSH, it's still used in controlled environments or labs for learning and testing.

---

## 🛠️ Project Explanation: Telnet Configuration

**Router Configuration:**
```bash
interface fa1/0
ip address 192.17.10.1 255.255.255.0
no shutdown
interface fa0/0
ip address 192.17.20.1 255.255.255.0
no shutdown
```

**Switch Configuration:**
```bash
interface vlan 1
ip address 192.17.20.252 255.255.255.0
no shutdown
exit
ip default-gateway 192.17.20.1
enable password mew
ip domain name my.com
username Admin password nahim
line vty 0 15
login local
transport input telnet
---

## 🔢 Telnet Connection Example
From another device (Admin PC):
```bash
telnet 192.17.20.252
Admin
nahim
enable
mew
```
You’ll be prompted to enter the password set earlier.

---

## 🚫 Telnet vs SSH
| Telnet | SSH |
|--------|-----|
| Sends data in plain text | Encrypts data |
| Less secure | More secure |
| Used in test environments | Preferred for production |

---

## 🔗 Best Practices
- Use Telnet **only** in trusted, secure, or lab environments.
- For real-world deployments, prefer **SSH**.
- Disable Telnet if not in use: 
```bash
line vty 0 15
transport input ssh
```

---

## 🔍 Verification Commands
```bash
show running-config | include vty
show line vty 0
```
These help you check Telnet configurations.

---

## 🔗 Additional Resources
- [Cisco VTY Configuration Guide](https://www.cisco.com/c/en/us/support/docs/ios-nx-os-software/ios-software-releases-122-mainline/55684-convtelssh.html)
- [Cisco CLI Telnet Reference](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/security/d1/sec-d1-cr-book/sec-cr-d1.html)

---