# 📼 Telnet Configuration Guide

## 📄 What is SSH?
**SSH** (short for *Secure Shell*) is a protocol used to remotely access and manage devices over a network using a command-line interface. It is highly secured comapare to Telnet!! it's used in controlled environments or labs for learning and testing.

---

## 🛠️ Project Explanation: SSH Configuration

**Router Configuration:**
```bash
interface fa0/0
ip address 192.17.1.1 255.255.255.0
no shutdown
interface fa1/0
ip address 192.17.2.1 255.255.255.0
no shutdown
```

**Switch Configuration:**
```bash
interface vlan 1
ip address 192.17.1.247 255.255.255.0
no shutdown
exit
ip default-gateway 192.17.1.1
enable password mew
ip domain name my.com
username Admin password nahim
crypto key generate rsa
ip ssh version 2
line vty 0 15
login local
transport input ssh
---

## 🔢 SSH Connection Example
From another device (Admin PC):
```bash
ssh -l Admin 192.17.1.247
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