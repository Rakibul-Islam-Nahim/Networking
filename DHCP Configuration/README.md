# 📄 DHCP Configuration Guide

## 💡 What is DHCP?

**DHCP (Dynamic Host Configuration Protocol)** is a network management protocol used to automatically assign IP addresses and other network configuration parameters (such as subnet mask, gateway, and DNS) to devices on a network. This simplifies the process of IP address management and reduces the potential for conflicts.

---

## 🛠️ How DHCP Works

1. **DHCP Discover:** The client broadcasts a request for an IP configuration.
2. **DHCP Offer:** The server responds with an available IP and configuration details.
3. **DHCP Request:** The client requests the offered IP address.
4. **DHCP Acknowledgment:** The server confirms and leases the IP address.

---

## 🔧 Project Explanation: DHCP Configuration

```bash
interface fa0/0
ip addresss 172.17.10.1 255.255.255.0
no shutdown
exit
ip dhcp excluded-address 172.17.10.1 172.17.10.10
ip dhcp pool nahim
network 172.17.10.0 255.255.255.0
default-router 172.17.10.1
```

### Explanation:

- `ip dhcp pool LAN_POOL`: Creates a DHCP pool.
- `network`: Defines the network range.
- `default-router`: Assigns the default gateway.
- `dns-server`: Provides DNS settings to clients.
- `lease`: Defines the lease duration in days.
- `excluded-address`: Reserves IP addresses from being assigned to clients.

---

## 🔐 Verifying DHCP Configuration

```bash
Router# show ip dhcp binding
Router# show ip dhcp pool
Router# show running-config | include dhcp
```

These commands verify DHCP bindings, statistics, and active configurations.

---

## 👥 Best Practices

- Exclude router and static IP addresses from the DHCP pool.
- Use short lease durations for guest or temporary networks.
- Document DHCP scope and exclusions clearly.
- Monitor address pool utilization regularly.

---

## 🔗 Additional Resources

- [Cisco DHCP Configuration Guide](https://www.cisco.com/c/en/us/support/docs/ip/dynamic-address-allocation-resolution/12480-29.html)
- [RFC 2131 - Dynamic Host Configuration Protocol](https://tools.ietf.org/html/rfc2131)

---
