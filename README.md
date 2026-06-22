# gns3
labs
# 🖧 OSPF Stub Area Lab Project

## 📌 Project Overview
This lab demonstrates how to configure an **OSPF Stub Area** in a multi‑router topology using GNS3.  
Stub areas reduce routing overhead by blocking external LSAs and relying on a default route injected by the ABR.

---

## 🗂 Topology
- **Area 0 (Backbone):** Routers R1–R4  
- **Area 1 (Stub):** Routers R5 (ABR) and R6 (internal)  
- **LANs/Subnets:**  
  - R5 ↔ R6: `172.16.1.0/24`  
  - R6 LAN: `10.0.0.0/24`  
  - R5 ↔ Backbone: connected to Area 0  

---

## ⚙️ Configuration

### R5 (ABR)
```bash
router ospf 1
 router-id 6.6.6.6
### R6
router ospf 1
 router-id 5.5.5.5
 network 10.0.0.0 0.0.0.255 area 1
 network 172.16.1.0 0.0.0.255 area 1
 area 1 stub
 network 172.16.1.0 0.0.0.255 area 1
 area 1 stub no-summary
