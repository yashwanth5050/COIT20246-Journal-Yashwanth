# Week 3 Journal – Network Technologies

**Student Name:** Yashwanth  
**GitHub:** https://github.com/yashwanth5050  
**Unit:** COIT20246 Networking and Cyber Security  
**Week:** 3  
**Topic:** Network Technologies

## Activity 1 – Identifying Network Interface Information

### Objective

The first Week 3 activity was to inspect the network interface more closely and identify information associated with the link layer.

### Commands Used

I used the following command:

```powershell
getmac /v
```

I also used:

```powershell
Get-NetAdapter | Select-Object Name, InterfaceDescription, MacAddress, LinkSpeed, Status
```

### Observations

The output included the MAC address of each adapter. I learned that an IP address and a MAC address serve different purposes. The IP address is used for logical network addressing and routing, while the MAC address identifies an interface at the local network/link layer.

The `LinkSpeed` field also showed the negotiated link speed reported by Windows. I understood that the advertised or negotiated link speed does not guarantee that every application will achieve that exact throughput because actual performance is affected by overhead, congestion, wireless conditions and other factors.

### Evidence

![Figure 3.1 – Network adapter MAC address and link information](images/week03-adapter-details.png)

**Figure 3.1 explanation:** This screenshot shows the MAC address, status and link speed of my network adapter.

## Activity 2 – Examining Ethernet and IP Information in Wireshark

### Objective

The aim of this activity was to examine a captured packet and distinguish between link-layer and network-layer addressing.

### Procedure

I started Wireshark on the active network interface and generated traffic using:

```powershell
ping 8.8.8.8
```

I applied the display filter:

```text
icmp
```

I selected an Echo Request packet and expanded the protocol information.

I examined:

```text
Frame
Ethernet II
Internet Protocol Version 4
Internet Control Message Protocol
```

### Observations

The Ethernet section contained source and destination MAC addresses. The IPv4 section contained source and destination IP addresses.

This showed me that a single packet can be described at several layers. The Ethernet frame is concerned with delivery over the current local link, while the IP packet is used for logical delivery across networks.

### Evidence

![Figure 3.2 – Ethernet and IPv4 details in Wireshark](images/week03-ethernet-ip.png)

**Figure 3.2 explanation:** This screenshot shows the Ethernet and IPv4 sections of a captured packet and demonstrates the difference between MAC and IP addressing.

## Activity 3 – Viewing the ARP Cache

### Objective

The purpose of this activity was to examine the relationship between IPv4 addresses and MAC addresses on the local network.

### Commands Used

I displayed the ARP cache using:

```powershell
arp -a
```

I also used PowerShell:

```powershell
Get-NetNeighbor
```

### Interpretation

The output contained local IP addresses associated with physical addresses. I learned that ARP is used on IPv4 local networks to determine the MAC address associated with an IPv4 address.

This is necessary because software may know the destination IP address, but Ethernet communication on the local network still needs an appropriate link-layer destination address.

### Evidence

![Figure 3.3 – ARP cache displayed in Windows](images/week03-arp-cache.png)

**Figure 3.3 explanation:** This screenshot shows IPv4 neighbour entries and their corresponding physical addresses.

## Activity 4 – Observing ARP Traffic in Wireshark

### Objective

The aim was to observe ARP directly in a packet capture.

### Procedure

I opened Wireshark and started a capture. I applied this display filter:

```text
arp
```

I generated normal local network traffic and observed available ARP packets.

Where necessary, I displayed the current ARP information using:

```powershell
arp -a
```

### Observations

ARP request messages are used to ask which device owns a particular IPv4 address, while ARP replies provide the associated MAC address.

This activity helped me understand why ARP is important in an Ethernet-based IPv4 LAN. IP provides logical addressing, but ARP provides the information required to deliver a frame to a local device.

### Evidence

![Figure 3.4 – ARP packets captured in Wireshark](images/week03-wireshark-arp.png)

**Figure 3.4 explanation:** This screenshot shows ARP traffic captured on the local network and illustrates the exchange used to associate IPv4 addresses with MAC addresses.

## Activity 5 – Creating a Basic Network Diagram

### Objective

The purpose of this activity was to represent a small network visually using diagrams.net/draw.io.

### Diagram

I created a simple network containing an end-user computer, a switch, a wireless access point/router and an Internet connection.

```text
+------------------+
| Yashwanth's PC   |
+--------+---------+
         |
         | Ethernet / Wi-Fi
         |
+--------+---------+
| Local LAN Device |
| Router / AP      |
+--------+---------+
         |
         | WAN
         |
+--------+---------+
|    Internet      |
+------------------+
```

In diagrams.net, I represented the devices as separate nodes and connected them with lines. I labelled the local network and WAN portions so that the path was clear.

### Evidence

![Figure 3.5 – Basic network topology created in diagrams.net](images/week03-network-diagram.png)

**Figure 3.5 explanation:** This diagram represents my understanding of a basic local network and how a host reaches the Internet through a local network device.

### Interpretation

The diagram helped me distinguish between an end device and networking infrastructure. A host generates or receives application data, while switches, access points and routers provide connectivity. The router is especially important because it provides a path between the local network and other IP networks.

## Activity 6 – Comparing Common Network Technologies

### Ethernet

Ethernet is commonly used for wired local area networking. It provides link-layer communication and uses MAC addresses within the local network. A wired Ethernet connection is normally stable and is not affected by radio interference in the same way as Wi-Fi.

### Wi-Fi

Wi-Fi provides local network communication using radio rather than a physical Ethernet cable. It gives users mobility and simplifies connections for laptops and mobile devices. However, the quality of a wireless connection can depend on distance, obstacles, interference and the capabilities of the access point and client device.

### Router

A router forwards packets between different IP networks. In a typical home or small-office environment, the router connects the private local network to an upstream Internet service.

### Switch

A switch connects devices within an Ethernet LAN and forwards Ethernet frames based on link-layer information. This differs from a router, which is primarily responsible for forwarding packets between IP networks.

### Evidence

![Figure 3.6 – Completed Week 3 network technology notes](images/week03-network-notes.png)

**Figure 3.6 explanation:** This screenshot shows my Week 3 Markdown entry containing the comparison of Ethernet, Wi-Fi, switching and routing concepts.

## Problems and Troubleshooting

The main difficulty in Week 3 was separating the purpose of MAC addresses from the purpose of IP addresses. Looking at one packet in Wireshark helped resolve this because both types of address were visible at the same time but in different protocol sections.

Another issue was that ARP captures are not always continuously visible because ARP mappings can already exist in the operating system cache. I therefore checked the existing neighbour table with `arp -a` and observed ARP traffic when it appeared during normal local network activity.

## Weekly Reflection

Week 3 improved my understanding of network technologies by showing how several layers work together. I previously understood an IP address mainly as the address of a computer on a network. The practical work showed me that local Ethernet communication also depends on MAC addresses and that ARP provides a connection between IPv4 addressing and link-layer delivery.

Wireshark was particularly useful because it allowed me to expand the Ethernet, IPv4 and ICMP sections of a real captured packet. This made the layered design of networking easier to understand than reading about each protocol independently.

Creating a network diagram also helped me organise the concepts visually. I can now more clearly explain the roles of an end device, switch, wireless access point and router.

Across the first three weeks, my approach has changed from simply running commands to interpreting what each command or packet tells me about the system. I expect this will be useful in later topics because network troubleshooting and cyber security both depend on understanding normal system and network behaviour first.
