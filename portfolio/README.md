# Royal-1 Technology Solutions | Network Design & Integration Portfolio

**LaVon Thomas · Cisco Packet Tracer · Completed October 29, 2026**

Two independently completed network designs became one integrated campus, branch, and Enterprise lab. This portfolio shows the original design scopes and the integration work that made cross-site web access, email, and calling work through site firewalls.

## Design 1 — Original Royal campus and branch

![Original Royal campus and branch topology](designs/01-campus-branch/images/original-campus-branch-topology.png)

## Design 2 — Original Enterprise campus

![Original Enterprise campus topology](designs/02-enterprise/images/original-enterprise-topology.png)

## Design 3 — Integrated Intersite-Lab

![Final integrated Packet Tracer topology](designs/03-integrated/images/final-intersite-topology.png)

## Three designs, one engineering story

| Stage | Design | Focus | Documentation |
|---|---|---|---|
| 1 | Royal campus and branch | Department segmentation, router-on-a-stick, DHCP, branch routing, voice | [Campus and branch](designs/01-campus-branch/README.md) |
| 2 | Enterprise campus | Four-floor topology, OSPF core, /26 VLANs, HSRP gateways, services and voice | [Enterprise](designs/02-enterprise/README.md) |
| 3 | Integrated Intersite-Lab | Combine both networks; add Enterprise firewall and edge router; validate cross-site services | [Integrated design](designs/03-integrated/README.md) |

All three screenshots are actual Packet Tracer captures supplied by the project owner. The original campus/branch capture shows `Royal Enterprise network.pkt`; the original Enterprise capture shows `Royal-Technology-Solutions-Enterprise-Network.pkt`; the integrated capture shows `Royal-1-InterSite-Lab.pkt`. All three matching owner-supplied `.pkt` projects are included below. Earlier repository project files and evidence remain as historical material.

## Download the three Packet Tracer projects

| Design | Project |
|---|---|
| 1 — Royal campus and branch | [Royal-Campus-Branch.pkt](designs/01-campus-branch/Royal-Campus-Branch.pkt) |
| 2 — Enterprise campus | [Royal-Enterprise-Campus.pkt](designs/02-enterprise/Royal-Enterprise-Campus.pkt) |
| 3 — Integrated Intersite-Lab | [Royal-1-InterSite-Lab.pkt](designs/03-integrated/Royal-1-InterSite-Lab.pkt) |

Use GitHub's **Download raw file** control to download a project, then open it in Cisco Packet Tracer. Files are preserved unchanged as supplied. They were not reopened in Packet Tracer during packaging; functional evidence comes from the project session and final owner confirmation.

## What I implemented

- Connected Royal campus/branch and Enterprise networks through a simulated provider/cloud router.
- Preserved the existing Enterprise floor uplinks while adding an ASA 5506-X firewall and a Cisco 2911 edge router.
- Configured /30 transit networks, static routes, OSPF redistribution, and a passive OSPF transit interface.
- Used departmental data and voice VLANs, HSRP virtual gateways, DHCP/DNS services, and Cisco call-manager dial peers.
- Configured service-specific firewall permissions for ICMP, DNS, HTTPS, and H.323 signaling.
- Consolidated simulated mail to a shared server and validated intersite message delivery and replies.

## Integrated perimeter

```mermaid
flowchart TB
  A[Royal campus and branch] --> B[ROYAL-FW01]
  B --> C[CLOUD-RTR]
  C --> D[ENTERPRISE-FW01]
  D --> E[ENTERPRISE-EDGE-RTR]
  E --> F[Enterprise core and VLANs]
  C --> G[Shared email server]
```

The old direct CLOUD-RTR–core serial connection remains administratively shut down. The active path crosses the Enterprise firewall. Re-enabling the old link would create a preferred bypass because its retained static routes have a lower administrative distance.

## Results

| Capability | Evidence |
|---|---|
| Cross-site IP reachability | Captured successful endpoint pings; owner confirmed all-PC reachability at completion |
| HTTPS in each direction | Campus accessed 192.168.12.198; Enterprise accessed 192.168.8.18 |
| Email | Cross-site send, receive, and reply confirmed |
| Voice | Successful cross-site call; final owner confirmation of calling service |
| Routing | Captured route tables showed the new firewall/edge path selected |

## Problems I investigated

Address overlap required renumbering the branch student subnet to 192.168.210.0/24. Copied sticky MAC entries required targeted port-security recovery. The new edge transit network needed an internal OSPF advertisement for return reachability. Simulation-mode packet inspection identified HTTPS drops at the ASAs. Explicit, narrowly scoped source-port-443 reply rules restored the tested web sessions. A later outside-link reset restored next-hop ARP learning before final end-to-end success.

I documented observations separately from root-cause conclusions: the intermittent serial and forwarding failures were not conclusively attributed to a specific cause.

## Technical record and scope

See the [architecture, addressing, routing, ACLs, and recovery record](docs/architecture-and-operational-record.md).

This is a Packet Tracer lab portfolio. The cloud segment is simulated routing, not AWS or an IPsec VPN. Teams/Microsoft 365 were an analogy for intersite collaboration, not deployed applications. The separate Royalty.Local and Royal1.Local Windows labs are not connected to this simulation. The recorded HTTPS reply rules cover the two tested clients, not every PC. Final functional completion is owner-confirmed; long-duration availability and failover testing are not claimed.

**Repository preparation:** See [publishing notes](publishing/PUBLISHING.md) for the remaining source files and release steps.
