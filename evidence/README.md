# Network Validation Evidence

This directory contains screenshots captured during verification of the working Cisco Packet Tracer network.

The evidence demonstrates VLAN configuration, 802.1Q trunking, router-on-a-stick, DHCP operation, RIPv2 dynamic routing, inter-VLAN connectivity, and communication with remote networks.
### Router-on-a-Stick Configuration
![Router-on-a-Stick Configuration](router-on-a-stick-configuration.png)

The main-campus router uses router-on-a-stick to provide inter-VLAN routing. IEEE 802.1Q subinterfaces are configured for VLANs 10 through 80, with each subinterface serving as the default gateway for its corresponding departmental network.

### RIPv2 Dynamic Routing
![RIPv2 Routing Verification](ripv2-routing-verification.png)

Cisco IOS verification confirms that RIPv2 is configured as the dynamic routing protocol. RIPv2 allows the main-campus router to exchange routing information with remote network infrastructure and provides reachability to remote networks across the WAN.
