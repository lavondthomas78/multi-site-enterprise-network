# multi-site-enterprise-network
## Overview

This project demonstrates the design and implementation of a multi-site enterprise network using Cisco Packet Tracer. The network was built to support multiple departmental VLANs at the main campus, centralized DHCP addressing, inter-VLAN communication, and routed connectivity to remote networks.

The design uses 802.1Q trunking and router-on-a-stick for communication between VLANs. RIPv2 provides dynamic routing between the main campus and remote networks across WAN links.

The project was validated through Cisco IOS commands and end-device connectivity testing to confirm that the major network services and routing functions were operating as intended.
## Key Technologies & Features

- Cisco Packet Tracer
- IPv4 addressing and subnetting
- Departmental VLAN segmentation
- IEEE 802.1Q trunking
- Router-on-a-stick inter-VLAN routing
- Router-based DHCP services
- RIPv2 dynamic routing
- Serial WAN connectivity
- Multi-site network communication
- Cisco IOS configuration and verification
- End-to-end ICMP connectivity testing
  ## Network Architecture

The network uses a multi-site architecture consisting of a main campus and remote network locations connected through routed WAN links.

At the main campus, eight VLANs separate departmental traffic into individual IPv4 networks. An 802.1Q trunk connects the campus switching infrastructure to the main campus router. The router uses subinterfaces to provide default gateways and router-on-a-stick inter-VLAN routing for each VLAN.

### Main Campus VLANs

| VLAN | Network | Default Gateway |
|------|---------|-----------------|
| 10 | 192.168.1.0/24 | 192.168.1.1 |
| 20 | 192.168.2.0/24 | 192.168.2.1 |
| 30 | 192.168.3.0/24 | 192.168.3.1 |
| 40 | 192.168.4.0/24 | 192.168.4.1 |
| 50 | 192.168.5.0/24 | 192.168.5.1 |
| 60 | 192.168.6.0/24 | 192.168.6.1 |
| 70 | 192.168.7.0/24 | 192.168.7.1 |
| 80 | 192.168.8.0/24 | 192.168.8.1 |

The main campus router also provides DHCP services for the departmental networks. RIPv2 dynamically exchanges routing information across the WAN, allowing the main campus to learn routes to remote networks such as 192.168.9.0/24 and 192.168.10.0/24.
## Implementation & Validation

The completed network was tested at both the infrastructure and end-device levels. Cisco IOS verification commands were used to confirm VLAN membership, trunk operation, interface status, DHCP configuration, and dynamic routing.

### Verified Results

- VLANs 10 through 80 were confirmed active on the main campus switching infrastructure.
- The switch-to-router connection was verified as an active 802.1Q trunk carrying the departmental VLANs.
- Router subinterfaces were configured for VLANs 10 through 80 and were verified in an up/up state.
- DHCP successfully assigned PC0 the IPv4 address 192.168.1.2/24 with a default gateway of 192.168.1.1.
- RIPv2 was verified as the active dynamic routing protocol.
- Remote networks 192.168.9.0/24 and 192.168.10.0/24 were dynamically learned through RIP.
- PC0 successfully reached a host at 192.168.2.2 on another VLAN, validating host-to-host inter-VLAN communication.
- PC0 successfully reached the remote host at 192.168.10.2, validating routed communication between the main campus and remote network.

### Connectivity Testing

Inter-VLAN testing between 192.168.1.2 and 192.168.2.2 completed successfully with 0% packet loss on the final test.

Remote connectivity testing between 192.168.1.2 and 192.168.10.2 also completed successfully with 0% packet loss on the final test. This demonstrates that traffic could traverse the local VLAN infrastructure, router-on-a-stick configuration, dynamic routing environment, and WAN path to reach a remote endpoint.
## Security Considerations

The current implementation focuses primarily on network functionality, segmentation, routing, addressing, and multi-site connectivity. During validation, access control lists (ACLs), SSH-based device administration, and local administrative user authentication were not configured on the main campus router.

Rather than representing these controls as implemented features, they are documented as opportunities for future security hardening.

### Future Security Enhancements

- Implement extended ACLs to restrict unnecessary communication between departmental VLANs.
- Protect sensitive networks such as IT, administrative, and server infrastructure from unauthorized departmental access.
- Configure SSH for encrypted remote administration of routers and switches.
- Implement local administrative accounts and enable secret protection.
- Apply switch port security to appropriate access ports.
- Disable and administratively shut down unused switch ports.
- Create a dedicated management VLAN for network infrastructure.
- Review device access and management permissions using the principle of least privilege.
- Test security controls to verify that authorized traffic is permitted while unauthorized traffic is denied.
  ## Project Files & Evidence

This repository includes the working Cisco Packet Tracer project along with screenshots collected during configuration verification and connectivity testing.

### Evidence Included

- Complete multi-site network topology
- VLAN configuration verification
- 802.1Q trunk verification
- Router subinterface configuration
- DHCP configuration and client addressing
- RIPv2 routing configuration
- Dynamic routing table verification
- Inter-VLAN host-to-host connectivity testing
- Main-campus-to-remote-network connectivity testing

The Cisco Packet Tracer `.pkt` file is included so the network topology and configuration can be examined directly in Packet Tracer.

## Lessons Learned

This project strengthened my understanding of how individual networking technologies work together in a larger enterprise environment. Configuring VLANs alone does not create communication between departments; switching, trunking, Layer-3 gateways, DHCP, dynamic routing, and WAN connectivity must work together for end-to-end communication.

Testing the completed network also reinforced the importance of verifying a design at multiple levels. Cisco IOS commands were used to confirm the infrastructure configuration, while end-device testing demonstrated that the configured network could successfully carry traffic between VLANs and across remote networks.

The security review also identified areas where a functional network can be improved through additional hardening. A future version of this project will focus on implementing and validating stronger access controls and secure device-management practices.

## Author

**LaVon Thomas**  
Computer Information Systems — Cybersecurity
