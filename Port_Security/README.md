# 🔒 Port Security Configuration Guide

## 📄 What is Port Security?

**Port security** is a Layer 2 security feature used on switch ports to restrict and control access based on MAC addresses. It helps prevent unauthorized devices from connecting to the network through a specific port.

---

## 💡 Why Use Port Security?

- 🛡️ Prevents unauthorized access to the network
- 🚫 Limits the number of MAC addresses on a port
- 🔐 Protects against MAC flooding attacks
- 🧰 Helps in maintaining network integrity and audit control

---

## 🛠️ Project Explanation: Port Security

### Shutdown All unused port First:

```bash
interface range fa3/1-fa5/1
shutdown
```

### Basic Configuration Example:

```bash
interface fa0/1
switchport mode access
switchport port-security
switchport port-security maximum 1
switchport port-security violation protected
switchport port-security mac-address sticky
interface fa1/1
switchport mode access
switchport port-security
switchport port-security maximum 1
switchport port-security violation restrict
switchport port-security mac-address sticky
interface fa2/1
switchport mode access
switchport port-security
switchport port-security maximum 1
switchport port-security violation shutdown
switchport port-security mac-address sticky
```

### Explanation:

- `switchport mode access`: Sets the port as an access port.
- `switchport port-security`: Enables port security.
- `maximum 1`: Allows only one MAC address.
- `violation shutdown`: Shuts down the port on a violation.
- `mac-address sticky`: Learns and stores the first MAC address dynamically.

---

## 🔐 Violation Modes

| Mode         | Description                                                             |
| ------------ | ----------------------------------------------------------------------- |
| **Protect**  | Discards traffic from unknown MAC addresses without notifying the admin |
| **Restrict** | Discards traffic and logs the violation                                 |
| **Shutdown** | Shuts the port down completely (default behavior)                       |

---

## 🔍 Verification and Monitoring

```bash
show port-security interface fa0/1
show port-security address
show running-config interface fa0/1
```

These commands help monitor and verify port security status and learned MAC addresses.

---

## 👥 Best Practices

- Enable port security on all access ports.
- Must be shutdown other unused port.
- Use `sticky` MAC addresses for ease of learning and persistence.
- Regularly monitor logs for violation events.
- Document authorized devices and their MAC addresses.

---

## 🔗 Additional Resources

- [Cisco Port Security Configuration Guide](https://www.cisco.com/c/en/us/support/docs/lan-switching/port-security/12062-12.html)
- [Cisco Catalyst Switches Port Security](https://www.cisco.com/c/en/us/products/collateral/switches/campus-lan-switches/white-paper-c11-740449.html)

---
