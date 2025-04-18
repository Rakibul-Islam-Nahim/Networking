# 📚 Understanding VLSM (Variable Length Subnet Masking)

## 📌 What is VLSM?
**VLSM (Variable Length Subnet Masking)** is a technique used to divide an IP address space into subnets of different sizes, based on the specific needs of the network.  
Unlike fixed subnetting, VLSM allows efficient use of IP addresses by allocating exactly as many addresses as needed.

---

## 🎯 Why Use VLSM?
- Efficient IP address utilization
- Flexible subnet design
- Better network organization
- Reduces IP wastage
- Allows hierarchical network design

---

## 🛠 How VLSM Works

1. **Determine the Number of Subnets Needed:**  
   Identify how many networks and hosts per network you require.

2. **Sort Requirements:**  
   List the subnets in **descending order** based on the number of hosts.

3. **Assign Subnets:**  
   Start from the largest subnet and assign the smallest possible network that can accommodate it.

4. **Update and Repeat:**  
   Move to the next subnet, adjusting the available IP range.

---

## ✍️ Project Explanation

I am working with a given network of `192.17.168.0/24` and all I need to subnetting it, such that:

| Subnet | Number of Hosts |
|:------:|:---------------:|
| A      | 37              |
| B      | 72              |
| C      | 46              |

### Step 1: Calculate Required Subnet Sizes
- A needs 37 hosts → requires a /26 (supports 62 hosts)
- B needs 72 hosts → requires a /25 (supports 126 hosts)
- C needs 46 hosts → requires a /26 (supports 62 hosts)

### Step 2: Assign Subnets
| Subnet | Network Address | Subnet Mask | Host Range | Broadcast Address |
|:------:|:---------------:|:-----------:|:----------:|:-----------------:|
| A | 192.17.168.128| 255.255.255.192 (/26) | 192.17.168.129 - 192.17.168.190| 192.17.168.191 |
| B | 192.17.168.0  | 255.255.255.128 (/25) | 192.17.168.1  - 192.17.168.126 | 192.17.168.127 |
| C | 192.17.168.192| 255.255.255.192 (/26) | 192.17.168.193 - 192.17.168.254| 192.17.168.255 |

---

## 🗌 Key Points to Remember
- Always assign IP addresses starting with the largest subnet requirement.
- Leave no overlaps between subnets.
- Always check network address and broadcast address.
- VLSM requires **classless routing protocols** (e.g., RIPv2, OSPF, EIGRP).

---

## 🔗 Additional Resources
- [Cisco VLSM Guide](https://www.cisco.com/c/en/us/support/docs/ip/routing-information-protocol-rip/13788-3.html)
- [IP Addressing and Subnetting for New Users](https://www.cisco.com/c/en/us/support/docs/ip/open-shortest-path-first-ospf/13788-3.html)

---

