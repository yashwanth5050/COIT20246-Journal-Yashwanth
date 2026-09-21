# Week 5 Journal – Internetworking

**Student Name:** Yashwanth. **GitHub:** https://github.com/yashwanth5050. **Unit:** COIT20246 Networking and Cyber Security. **Week:** 5. **Topic:** Internetworking.

## Activity 1 – Viewing and Interpreting the Windows Routing Table

### Objective

This was to see the routing table of the window computer and to learn how windows determines where to route packets.

### Work Completed

Using the route print command in PowerShell, I looked at the routing information and noted the destination network and the prefix or netmask, gateway, interface and metric values. The default route is designated by 0.0.0.0/0 and is used when none of the specified routes are a more specific match for a destination. A directly connected LAN route refers to the subnet that is connected to the local physical interface and the packets can be delivered to hosts in the subnet without an external router. When the OpenWRT virtual machine is running the host-only network as created by VirtualBox will also be listed as a directly connected network.

The subnet of 127.0.0.0/8 is used for loopback communications towards the local computer. IPv4 multicast traffic uses the route 224.0.0.0/4 and 255.255.255.255/32 is the limited broadcast address. The source routing metric when alternatives routes are otherwise acceptable, but if there are two acceptable routing prefixes then the more specific can be chosen.

### Interpretation

The routing table revealed that not all packets are sent to the default gateway within a computer. Either directly connected or remote networks may be serviced from the local interface, and remote networks will be serviced from a router. Important distinction because it is the difference between communication in local LAN environment and an environment requiring communication to be traversed across an internetwork.

The second activity involves IP network design.The second exercise is to design an IP network.

### Objective

This activity was intended for the following: Design a small test internetwork comprising of 2 switched Ethernet LANs with 2 routers in between and a point-to-point WAN link at 1 Gbps.

### Addressing Plan

All three IPv4 networks have a /24 netmask. LAN A uses network 50.50.10.0/24. PC-A1 uses 50.50.10.11/24, PC-A2 uses 50.50.10.12/24 and PC-A3 uses 50.50.10.13/24. The three LAN A computers are configured with default gateway 50.50.10.1/24, which is the configuration of the LAN interface of Router1.

The point to point WAN is on the network of 10.0.0.0/24. Router1 uses 10.0.0.1/24 on its WAN interface and Router2 uses 10.0.0.2/24 on its WAN interface. LAN B uses network 60.60.20.0/24. Router2 uses 60.60.20.1/24 on its LAN interface, while PC-B1 uses 60.60.20.11/24 and PC-B2 uses 60.60.20.12/24. The default gateway to use for the LAN B computers is thus 60.60.20.1.

Router1 has directly connected routes for 50.50.10.0/24 and 10.0.0.0/24, while traffic for 60.60.20.0/24 is forwarded to next hop 10.0.0.2. Router2 has directly connected routes for 60.60.20.0/24 and 10.0.0.0/24, while traffic for 50.50.10.0/24 is forwarded to next hop 10.0.0.1. The LAN A computers' direct route is to the network 50.50.10.0/24 with the default gateway being 50.50.10.1. The LAN B computers have a default gateway of 60.60.20.1 and use a direct route for the 60.60.20.0/24 network.

In this case, the sources (s) and destinations (d) for the hosts remain the same even when the packet is routed from PC-A1 (s=50.50.10.11) to PC-B1 (d=60.60.20.11). The Ethernet source address on LAN A is the address of PC-A1 and the Ethernet destination address on LAN A is the address of the LAN interface of Router1. Throughout the WAN, Router1 transmits a brand new Ethernet frame to the WAN interface of Router2. ROUTER2 forwards another Ethernet frame to PC-B1 out of LAN interface on LAN B. This indicates that the local link-layer addressing is changed due to routing but end-to-end IP addressing remains the same.

### Interpretation

The activity illustrated the need for routers if the hosts are on different IP networks. Ethernet traffic can be forwarded from a computer directly just in the local network segment. If the destination address is not a part of that subnet, the computer passes the packet on to its default gateway, which then sends the packet to its next hop/next network based on its routing information.

## Activity 3 – Academic Integrity Outcomes

### Objective

The aim of this activity was to reflect on what students can do to prevent academic integrity issues and what might be at stake if a student's academic integrity is compromised through copying, sharing or misrepresenting an academic task.

### Discussion Outcome

The one I found most helpful was a student using another student's assessment tools and as if they were their own. This form of behaviour may be plagiarism, collusion or sharing of inappropriate files, depending on the situation. CQUniversity may examine alleged violations and decide on a course of action based on their evidence and severity of the incident. This might involve an educational action, mark penalties, having to resubmit, failure of an assessment/unit or more severe action if the misconduct is severe.

One good approach that can prevent problems is to make copies of the personal draft(s), working files, and the Git commit history, to show the development of the work. The tutor should also be asked how much team working the student can do before they decide to give an answer for an assessment, files containing data, or final work to another student.

### Interpretation

The conversation confirmed that academic dishonesty means so much more than copying. Students must also refrain from working together without permission, copying or copying and pasting finished work and from plagiarising another student's work.

## Activity 4 – IP Address Lookup

### Objective

This activity was undertaken to see how an IP geolocation service will work when Internet connect is offered using various networks.

### Work Completed

I found out the result using a normal broadband connection to the result using a mobile network. In both cases, the service provided a public IP address on the Internet along with the Internet service provider/carrier and an estimated geographic area.

The reported location was not an exact street location. Broadband was identified by the provider network that was expected for the city or region; mobile may be identified in a different nearby region as the provider network may flow off their network via a gateway outside their provider network. The service has also failed to tell users of the private ip address (used in local LANs - doesn't normally get forwarded over the public network) on the block in question.

### Interpretation

This activity has demonstrated that IP geolocation is not a true location service but only a good estimation. It is helpful to use for country or region identification, provider or approximate city identification but it should not be used as confirmation that a user is in a physical location.

## Problems and Troubleshooting

Main challenge: Separated types of addressing. Routing is based on IP network and gateways, and Ethernet delivery is based on MAC address. After the packet was traversed through each routed link, it becomes apparent that the routers maintain the end to end IP address, while switching out the local ethernet address for the next hop.

## Weekly Reflection

Week 5 was where I got an understanding of how packets could travel outside of a single LAN. The Windows routing information propagated the same concept, and the IP design activity spread the IP concept to an internetwork of two LANs and a WAN.

The most useful was the fact that the forwarder does not take the destination IP address when a packet is forwarded. This hop passes on at the Ethernet level, and the next hop for the IP packet is the router. Academic Integrity and IP Lookup was found to involve not just technical configuration, but professional and privacy concerns as well as networking work.