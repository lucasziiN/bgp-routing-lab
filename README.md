# BGP Routing in a Mini-Internet – COMPX304 Assignment 2

A simulated BGP configuration project connecting a custom Autonomous System (AS) to others in a mini-Internet, using **FRRouting (FRR)**. This builds upon the OSPF-based internal network from Assignment 1 and adds **full BGP peering and policy routing**.

Developed as part of COMPX304 – Advanced Networking & Cyber Security at the University of Waikato (2025).

---

## 🌐 Objectives

- Establish **iBGP sessions** across internal routers
- Set up **eBGP peering** with multiple AS neighbors (providers, customers, peers, IXP)
- Configure **BGP route advertisements** using `/8` prefix
- Apply **community-based BGP policies** for traffic engineering
- Enforce real-world BGP economics: transit restrictions based on peer/provider/customer relationships
- Monitor reachability using **Looking Glass**, **Connectivity Matrix**, and **BGP Analyzer**

---

## 🧱 Network Overview

- Internal AS: 8 routers fully meshed using OSPF and iBGP
- External Links:
  - 2 Providers (inbound)
  - 2 Customers (outbound)
  - 1 Peer (Tier-2)
  - 1 IXP (Internet Exchange Point)
- BGP setup:
  - Internal routing via iBGP full mesh
  - External peering via eBGP
  - Loopback addresses used as router IDs

---

## 📁 Project Structure

COMPX304-A2/
├── configs/ # Saved router/host configs
├── step-6.txt # iBGP session verification
├── step-9.txt # IXP session and BGP table summary
├── bgp-policy.txt # Policy description and snapshots
└── README.md

---

## 🔧 Tools & Technologies

- 🖥️ **FRRouting (FRR)** on Linux-based virtual routers
- 🧭 `show ip bgp`, `show ip route`, `traceroute`, `ping`
- 📊 [Looking Glass Tool](https://mini.cms.waikato.ac.nz/looking-glass/)
- 📈 [Connectivity Matrix](https://mini.cms.waikato.ac.nz/matrix)
- 🧠 BGP Analyzer (Route leak detection)

---

## 🔄 Workflow Summary

### ✔️ iBGP Setup

- Loopback-based full mesh
- `update-source` set to loopbacks
- Verified using `show ip bgp summary`

### ✔️ eBGP Setup

- IXP peering via NEWY router
- Peers, providers, and customers configured using interface IPs

### ✔️ BGP Prefix Advertising

- /8 prefix advertised from all routers
- Blackhole route used to validate /8 advertisement
- Removed OSPF redistribution

### ✔️ IXP Route Maps

- Applied BGP communities via `route-map IXP_out`
- Communities like `122:23`, `122:25` used to reach IXP peers

### ✔️ Policy-Based Routing

- Classified routes with communities: customer, peer, provider
- Created route-maps like `TO_CUSTOMER`, `TO_PEER`, `FROM_PROVIDER`
- Verified exported/imported routes using Looking Glass

---

## 🧠 Learning Outcomes

- Real-world BGP route propagation and filtering
- FRRouting configuration and troubleshooting
- Network topology planning and policy implementation
- Using measurement and diagnostic tools for validation

---

## 👨‍🎓 Author

**Lucas Oda**  
Bachelor of Science (Computer Science Major)  
University of Waikato – COMPX304 (2025)

---

## 📄 License

For educational use only.
