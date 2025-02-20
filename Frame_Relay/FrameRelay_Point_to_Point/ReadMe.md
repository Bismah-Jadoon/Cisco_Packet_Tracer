## **Frame Relay Point-to-Point Configuration Guide**

Frame Relay is a high-performance WAN protocol that operates at the data link layer (Layer 2) of the OSI model. It is used to establish virtual circuits (VCs) between endpoints. One common Frame Relay configuration is **Point-to-Point**, which creates a dedicated virtual circuit between two locations.

---

### **1. Understanding Frame Relay Point-to-Point**
- A **Point-to-Point** connection in Frame Relay acts as a direct link between two routers.
- Unlike multipoint configurations, each point-to-point subinterface is treated as its own network segment.
- Each virtual circuit is associated with a **Data-Link Connection Identifier (DLCI)**, which acts as an address for the connection.

---

## **2. Frame Relay Point-to-Point Configuration**
### **Step 1: Enable Frame Relay on Serial Interface**
1. **Enable Frame Relay encapsulation**
2. **Create point-to-point subinterfaces**
3. **Assign IP addresses**
4. **Map DLCIs to the subinterfaces**
5. **Verify connectivity**

### **Network Topology**
```
[R1] -------- [Frame Relay Switch] -------- [R2]
  |                                            |
S0/0                                       S0/0
DLCI 102                                    DLCI 201
```

---

### **Step 2: Configure Frame Relay on R1**
```bash
R1# configure terminal
R1(config)# interface Serial0/0
R1(config-if)# encapsulation frame-relay
R1(config-if)# no shutdown

# Configure a point-to-point subinterface
R1(config-if)# interface Serial0/0.1 point-to-point
R1(config-subif)# ip address 192.168.1.1 255.255.255.252
R1(config-subif)# frame-relay interface-dlci 102
R1(config-subif)# exit
R1(config)# exit
```

---

### **Step 3: Configure Frame Relay on R2**
```bash
R2# configure terminal
R2(config)# interface Serial0/0
R2(config-if)# encapsulation frame-relay
R2(config-if)# no shutdown

# Configure a point-to-point subinterface
R2(config-if)# interface Serial0/0.1 point-to-point
R2(config-subif)# ip address 192.168.1.2 255.255.255.252
R2(config-subif)# frame-relay interface-dlci 201
R2(config-subif)# exit
R2(config)# exit
```

---

### **3. Verifying the Configuration**
#### **Check Frame Relay PVC Status**
```bash
R1# show frame-relay pvc
```
- Look for "ACTIVE" status, indicating a working connection.

#### **Check DLCI Mappings**
```bash
R1# show frame-relay map
```
- Displays mappings between DLCIs and IP addresses.

#### **Ping to Verify Connectivity**
```bash
R1# ping 192.168.1.2
```
- If successful, Frame Relay is configured correctly.

---

### **4. Troubleshooting Commands**
#### **Check Serial Interface Status**
```bash
R1# show interfaces serial 0/0
```
- Look for "Serial0/0 is up, line protocol is up."

#### **Check Frame Relay LMI Status**
```bash
R1# show frame-relay lmi
```
- Displays LMI (Local Management Interface) statistics.

#### **Check Routing Table**
```bash
R1# show ip route
```
- Ensures correct routing of packets.

---

## **Conclusion**
Frame Relay **point-to-point** subinterfaces allow dedicated virtual circuits for direct connectivity between two routers. The main steps include enabling Frame Relay encapsulation, configuring subinterfaces with DLCIs, assigning IP addresses, and verifying the configuration.
