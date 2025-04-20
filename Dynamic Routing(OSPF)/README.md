# 🌐 Understanding Dynamic Routing

## 📄 What is Dynamic Routing?
**Dynamic routing** is a network technique where routers automatically exchange routing information to learn about remote networks and dynamically adjust to changes in network topology. Unlike static routing, dynamic routing updates itself without manual intervention.

---

## 💡 Why Use Dynamic Routing?
- 🔄 Automatically adapts to network changes
- 📊 Scales better for large and complex networks
- 🛡️ Supports redundancy and load balancing
- 🧬 Reduces manual configuration workload

---

## 🛠️ How Dynamic Routing Works
Routers share routing information with each other using routing protocols. Each router builds its own dynamic routing table based on the exchanged information.

**Key Components:**
- **Routing Protocol:** Language routers use to exchange information (e.g., OSPF, RIP)
- **Metric:** Value to determine the best path (e.g., hop count, bandwidth)
- **Convergence:** Time taken to update the routing table after a change

---

## 📈 Types of Dynamic Routing Protocols

| Protocol | Type | Metric Used | Best for |
|:--------:|:----:|:-----------:|:--------:|
| RIP (Routing Information Protocol) | Distance-Vector | Hop count | Small networks |
| OSPF (Open Shortest Path First) | Link-State | Cost (Bandwidth) | Medium to large networks |
| EIGRP (Enhanced Interior Gateway Routing Protocol) | Hybrid | Composite metric | Cisco networks |
| BGP (Border Gateway Protocol) | Path-Vector | Path attributes | Internet (ISP networks) |

---

## 👥 Advantages and Disadvantages

| Advantages | Disadvantages |
|:----------:|:-------------:|
| Self-adjusting to network changes | Higher CPU, memory, and bandwidth usage |
| Scalable to large topologies | More complex configuration |
| Supports multiple paths and redundancy | Risk of routing loops without safeguards |

---

## 🔍 Project Discussion: OSPF Configuration

**Router0 Configuration:**
```bash
router ospf 1
 network 192.17.30.0 0.0.0.255 area 1
 network 192.17.99.0 0.0.0.3 area 1
 network 192.17.99.8 0.0.0.3 area 1
```

**Router1 Configuration:**
```bash
router ospf 2
 network 192.17.10.0 0.0.0.255 area 1
 network 192.17.99.0 0.0.0.3 area 1
 network 192.17.99.4 0.0.0.3 area 1
```

**Router2 Configuration:**
```bash
router ospf 3
 network 192.17.20.0 0.0.0.255 area 1
 network 192.17.99.8 0.0.0.3 area 1
 network 192.17.99.4 0.0.0.3 area 1
```

This allows routers to dynamically share routes inside Area 1.

---

## 🛠️ Troubleshooting Dynamic Routing
- Use `show ip route` to view the routing table.
- Use `show ip protocols` to check running routing protocols.
- Use `debug ip routing` carefully to watch routing changes.

---

## 🔗 Additional Resources
- [Cisco Dynamic Routing Protocols Overview](https://www.cisco.com/c/en/us/tech/ip/dynamic-routing-protocols/index.html)
- [Networking Academy Dynamic Routing Course](https://www.netacad.com/)

---
