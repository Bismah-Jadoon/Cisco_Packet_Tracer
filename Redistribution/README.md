# Redistribution in Networking Complete Documentation

## Introduction to Redistribution in Networking
Redistribution in networking allows different routing protocols to share route information, enabling interoperability between networks running different protocols. It is used when an organization uses multiple routing protocols and needs seamless communication between them.

## Features
- Allows interoperability between different routing protocols
- Provides network flexibility and scalability
- Supports filtering and route summarization to control redistributed routes
- Can be implemented between OSPF, EIGRP, RIP, BGP, and other protocols

## Types of Redistribution
- **One-Way Redistribution**: Routes are shared in one direction only.
- **Two-Way Redistribution**: Routes are exchanged between two routing protocols bidirectionally.
- **Filtered Redistribution**: Routes are selectively advertised using filters.
- **Route Summarization**: Reduces the number of routes exchanged to improve efficiency.

## Configuring Route Redistribution
### Step 1: Enable Routing Protocols
```sh
router ospf 1
router eigrp 10
```

### Step 2: Configure Redistribution Between Protocols
#### OSPF to EIGRP
```sh
router eigrp 10
 redistribute ospf 1 metric 1000 100 255 1 1500
```

#### EIGRP to OSPF
```sh
router ospf 1
 redistribute eigrp 10 subnets
```

#### RIP to OSPF
```sh
router ospf 1
 redistribute rip metric 1 subnets
```

#### OSPF to BGP
```sh
router bgp 65001
 redistribute ospf 1
```

## Controlling Redistribution with Route Maps
To avoid routing loops and optimize redistribution, route maps are used:
```sh
route-map FILTER permit 10
 match ip address 1
 set metric 1000
router ospf 1
 redistribute eigrp 10 route-map FILTER
```

## Verifying Redistribution
| Command | Description |
|---------|-------------|
| `show ip route` | Displays the routing table |
| `show ip protocols` | Shows active routing protocols and redistribution details |
| `show ip ospf database` | Displays the OSPF database |
| `show ip eigrp topology` | Shows EIGRP topology table |

## Conclusion
Route redistribution enables seamless communication between different routing protocols by sharing routing information effectively. Proper implementation, filtering, and route summarization ensure efficient and stable network operations.

