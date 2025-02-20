# HSRP in Networking Complete Documentation

## Introduction to HSRP in Networking
Hot Standby Router Protocol (HSRP) is a Cisco proprietary redundancy protocol designed to provide high availability and failover capabilities for network routing. It ensures network stability by allowing a group of routers to work together and present a single virtual IP address to devices on the network.

## Features
- Provides automatic failover between routers
- Uses a virtual IP address for seamless traffic redirection
- Supports multiple HSRP groups for redundancy
- Load balancing with multiple HSRP instances
- Preemption for automatic restoration of primary router

## HSRP States
1. **Initial**: Router is starting up and not yet participating.
2. **Learn**: Router is waiting to receive Hello messages.
3. **Listen**: Router is listening for Hello messages from active and standby routers.
4. **Speak**: Router sends and receives Hello messages to determine roles.
5. **Standby**: Router is ready to take over if the active router fails.
6. **Active**: Router is forwarding traffic as the primary router.

## Configuring HSRP
### Step 1: Enable HSRP on the Primary Router
```sh
interface GigabitEthernet0/1
 ip address 192.168.1.1 255.255.255.0
 standby 1 ip 192.168.1.254
 standby 1 priority 110
 standby 1 preempt
```

### Step 2: Enable HSRP on the Standby Router
```sh
interface GigabitEthernet0/1
 ip address 192.168.1.2 255.255.255.0
 standby 1 ip 192.168.1.254
 standby 1 priority 100
 standby 1 preempt
```

### Step 3: Configure Authentication (Optional)
```sh
interface GigabitEthernet0/1
 standby 1 authentication md5 key-string hsrpKey
```

### Step 4: Verify HSRP Configuration
```sh
show standby brief
show standby
```

## HSRP Load Balancing
HSRP supports load balancing by configuring multiple groups:
```sh
interface GigabitEthernet0/1
 standby 1 ip 192.168.1.254
 standby 1 priority 110
 standby 1 preempt

interface GigabitEthernet0/2
 standby 2 ip 192.168.1.253
 standby 2 priority 105
 standby 2 preempt
```

## Verifying HSRP
| Command | Description |
|---------|-------------|
| `show standby` | Displays HSRP status and active/standby roles |
| `show standby brief` | Shows a summary of HSRP groups and priorities |
| `debug standby` | Enables real-time debugging of HSRP events |

## Conclusion
HSRP ensures high availability in networking by providing automatic failover between routers. Proper configuration of priorities, preemption, and authentication enhances network redundancy and reliability.

