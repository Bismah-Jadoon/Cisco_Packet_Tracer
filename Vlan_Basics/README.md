# VlanBasics
**VLAN Setup and Management in Cisco Packet Tracer**

This README provides an overview of setting up and managing VLANs (Virtual Local Area Networks) using Cisco Packet Tracer. VLANs are essential for network segmentation, improving performance, and enhancing security by isolating network traffic.

**Overview**

In this project, two VLANs were created:

VLAN-10 (IT)

VLAN-20 (Sales)

Devices were assigned to these VLANs to demonstrate how VLANs operate and how they influence communication within and across VLANs.

**Key Features**

Segmented network into two logical groups (IT and Sales).

Isolated traffic within the same VLAN.

Tested communication between devices in the same VLAN and across VLANs.

Commands Used

_**Creating a VLAN:**_

Enter Global Configuration Mode:

enable
configure terminal

_**Create a VLAN:**_

vlan [VLAN_ID]

_**Name the VLAN (optional):**_

name [VLAN_Name]

_**Assign Ports to VLAN:**_

interface [interface_id]
switchport mode access
switchport access vlan [VLAN_ID]

_**Deleting a VLAN:**_

Enter Global Configuration Mode:

configure terminal

_**Delete the VLAN:**_

no vlan [VLAN_ID]

**Communication Testing**

Within the Same VLAN: Devices communicate seamlessly as they are on the same Layer 2 domain.

Between Different VLANs: Requires a router or Layer 3 switch for inter-VLAN communication.

**Summary**

This project demonstrated how VLANs improve network management and security by isolating traffic into logical groups. Hands-on configuration in Cisco Packet Tracer solidifies understanding of essential networking concepts.

**Hashtags**

#Networking #VLAN #CiscoPacketTracer #ITSkills #NetworkEngineering

