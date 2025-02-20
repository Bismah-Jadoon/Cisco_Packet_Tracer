# Multiple Area OSPF Complete Documentation

## Introduction to Multiple Area OSPF
Open Shortest Path First (OSPF) is a link-state routing protocol that enables efficient and scalable routing in large networks. Multiple Area OSPF is an advanced implementation of OSPF that divides a large network into multiple areas to improve efficiency, reduce routing overhead, and enhance stability.

## Features
- Hierarchical design with backbone area (Area 0) and multiple non-backbone areas
- Faster convergence and reduced routing table size
- Scalability for large networks
- Improved stability by containing network changes within an area
- Supports route summarization to optimize routing updates

## OSPF Areas
OSPF divides a network into multiple areas:
- **Backbone Area (Area 0)**: The central hub that connects all other areas.
- **Regular Areas**: Connected to Area 0 and contain routers and subnets.
- **Stub Areas**: Restrict external route advertisements to reduce routing overhead.
- **Totally Stubby Areas**: Block both external and inter-area routes except for a default route.
- **Not-So-Stubby Areas (NSSA)**: Allow limited external route advertisements.

## OSPF Router Types
- **Internal Router (IR)**: Belongs to a single area and only has intra-area routes.
- **Area Border Router (ABR)**: Connects multiple areas and manages inter-area routing.
- **Autonomous System Boundary Router (ASBR)**: Connects to external networks and injects external routes into OSPF.

## OSPF Packet Types
1. **Hello Packet**: Establishes and maintains neighbor relationships.
2. **Database Description (DBD) Packet**: Exchanges database summaries between routers.
3. **Link-State Request (LSR) Packet**: Requests specific LSAs from neighbors.
4. **Link-State Update (LSU) Packet**: Sends updated LSAs to neighbors.
5. **Link-State Acknowledgment (LSAck) Packet**: Acknowledges receipt of LSU packets.

## Configuring Multiple Area OSPF
### Step 1: Enable OSPF
```sh
router ospf 1
```

### Step 2: Configure OSPF Areas
```sh
network 192.168.1.0 0.0.0.255 area 0
network 192.168.2.0 0.0.0.255 area 1
network 192.168.3.0 0.0.0.255 area 2
```

### Step 3: Configure an ABR
```sh
router ospf 1
 network 192.168.1.0 0.0.0.255 area 0
 network 192.168.2.0 0.0.0.255 area 1
```

### Step 4: Configure Route Summarization on ABR
```sh
router ospf 1
 area 1 range 192.168.2.0 255.255.255.0
```

### Step 5: Configure an ASBR for External Routes
```sh
router ospf 1
 redistribute connected subnets
```

## Verifying OSPF Configuration
| Command | Description |
|---------|-------------|
| `show ip ospf neighbor` | Displays OSPF neighbor relationships |
| `show ip ospf database` | Shows the OSPF link-state database |
| `show ip route ospf` | Displays OSPF learned routes |
| `show ip ospf interface` | Shows OSPF-enabled interfaces |

## Conclusion
Multiple Area OSPF provides an efficient and scalable routing solution for large networks. By dividing the network into multiple areas, OSPF reduces routing overhead, improves stability, and enhances network performance. Proper configuration of ABRs and ASBRs ensures optimal route summarization and external route injection.

