# 📍 Understanding Static Routing

## 📄 What is Static Routing?
**Static routing** is a method of routing where routes are manually configured and maintained by the network administrator. Unlike dynamic routing protocols, static routes do not change unless manually updated, providing full control over the network traffic path.

---

## 💡 Why Use Static Routing?
- 📈 Simple and predictable routing
- 📅 Ideal for small or stable networks
- 🔐 More secure since no routing advertisements are shared
- 💪 Lower CPU and bandwidth usage compared to dynamic routing

---

## 🛠️ How Static Routing Works
In static routing, the administrator manually defines the destination network, subnet mask, and the next-hop IP address or exit interface.

**Basic Syntax (Cisco IOS example):**
```bash
ip route [destination_network] [subnet_mask] [next_hop_ip_or_exit_interface]
```

**Example:**
```bash
ip route 192.168.2.0 255.255.255.0 10.0.0.2
```
This command tells the router: "To reach the 192.168.2.0/24 network, send packets to 10.0.0.2."

---

## 👥 Types of Static Routes
- **Standard Static Route:**
  - Manually configured with a specific destination and next-hop.

- **Default Route (Gateway of Last Resort):**
  - Used when no other route matches the destination IP address.
  - Example:
    ```bash
    ip route 0.0.0.0 0.0.0.0 [next_hop_ip]
    ```

- **Floating Static Route:**
  - Backup route with a higher administrative distance than the primary dynamic route.

---

## 🔗 Advantages and Disadvantages

| Advantages | Disadvantages |
|:----------:|:-------------:|
| Simple to configure | Not scalable for large networks |
| Predictable traffic flow | Manual updates required for changes |
| No routing overhead | Higher chance of human error |

---

## 📊 Project Explanation

**Network Topology:**
```
Network 1 -- Router0 -- Router2 -- Router3 -- Router4 -- Router1 -- Network 2
```

**Router0 Configuration:**
```bash
ip route 192.17.20.0 255.255.255.0 192.17.99.3
```

**Router2 Configuration:**
```bash
ip route 192.17.10.0 255.255.255.0 192.17.99.2
ip route 192.17.20.0 255.255.255.0 192.17.98.2
```

**Router3 Configuration:**
```bash
ip route 192.17.10.0 255.255.255.0 192.17.98.1
ip route 192.17.20.0 255.255.255.0 192.17.97.2
```

**Router4 Configuration:**
```bash
ip route 192.17.10.0 255.255.255.0 192.17.97.1
ip route 192.17.20.0 255.255.255.0 192.17.96.2
```

**Router1 Configuration:**
```bash
ip route 192.17.10.0 255.255.255.0 192.17.96.1
```
This setup enables PC1 to communicate with PC2 across the 5 routers.

---

## 🛠️ Troubleshooting Static Routes
- Use `show ip route` to verify routes.
- Use `ping` and `traceroute` commands to check connectivity.
- Check for correct subnet masks and next-hop addresses.

---

## 🔗 Additional Resources
- [Cisco Static Routing Guide](https://www.cisco.com/c/en/us/td/docs/ios/iproute/configuration/guide/ird_book/ird_static_routes.html)
- [Networking Academy: Static Routing](https://www.netacad.com/)

---