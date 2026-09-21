# Week 4 Journal – Network Technologies

**Student Name:** Yashwanth. **GitHub:** https://github.com/yashwanth5050. **Unit:** COIT20246 Networking and Cyber Security. **Week:** 4. **Topic:** Network Technologies.

## Activity 1 – Switched LAN Topologies

### Objective

The aim of this activity was to get an understanding to connect Ethernet end devices through the switches and how the bigger switched network can be organised from a single switching device.

### Work Completed

I thought about a small switched LAN with one switch, and 4PCs. The switch serves as the hub of traffic and each of the PC's (labelled PC1 thru PC4) has its own Ethernet connection to Switch1. The diagram illustrates the basic configuration of switched star LANs where each end device connects directly to the central switch.

Also under consideration was a larger switched LAN with 8 PCs and 3 switches. PC1 - PC4 are connected to Switch1, PC5 - PC8 are connected to Switch2. CoreSwitch is then connected to Switch1 and Switch2. This is an extension of basic switched LAN to allow multiple end devices in two clusters to be connected together through a central switching point.

### Interpretation

The activity proved that, a person could put devices belonging to the same Ethernet LAN to a switch which acts as a center point. It also demonstrated that a network could be extended by connecting the switches together. The PCs are considered end devices, having a function of sending and accepting application data, and the switches are considered intermediary devices whose function is to transport Ethernet frames between an appropriate pair of interfaces.

You will now analyse Ping, ARP and ICMP packets.Now you will generate and analyse Ping, ARP and ICMP packets.

### Objective

In this activity, it was intended to add some processing to the ping packet capture from the previous networking activity and to correlate the observed packets with addressing, protocol layering and encapsulation.

### Work Completed

In the previous Wireshark capture there was traffic that had a source host of 192.168.1.11, a destination host of 192.168.2.21, and a local gateway of 192.168.1.1. ICMP Echo Request	returns were selected with the following source and destination MAC addresses: 08:00:27:ef:bf:5e - 08:00:27:e9:b4:2f.

The ARP exchange had the question “Who has 192.168.1.1?” Tell 192.168.1.11” followed by the response “192.168.1.1 is at 08:00:27:e9:b4:2f.” For Ethernet, ARP is a necessity since Ethernet delivery implies MAC addressing on the local LAN. Before a host can transfer a frame to its neighbor, it must determine the neighbor's Mac address for the corresponding local IP address, or local IPv4 address. Thus, the host sends an ARP request for 192.168.1.1 and the device with this IPv4 address replies with its physical address.

The first ICMP packet was an Echo Request sent from 192.168.1.11 to 192.168.2.21. The previous capture had a frame length of 98 bytes and an IPv4 TTL of 64. This packet is a request by the sender for the remote host to reply with an ICMP Echo Reply.

The second ICMP packet was the Echo Reply sent from 192.168.2.21 back to 192.168.1.11 and that was the response for the first packet sent. It also had a frame length of 98 bytes and a visible TTL value of 63. Indicates that Echo Request has been received by the destination and received a response.

### Protocol Layering

Analyzing the captured traffic revealed that several protocols work in conjunction to allow ping to function. ARP supplies the local AR function to discover the next-hop mac address. This ICMP message is encapsulated within an IP version 4 packet and that one is encapsulated within the Ethernet frame for delivery on the local link.

The source and destination IP addresses (version 4) specify the communicating hosts within the internetwork. Because Ethernet source and destination addresses serve a more local function, they are used to refer to the sender and receiver on a particular link. Typical packet traversal of routers results in no change in the end-to-end IP addresses—only in the Ethernet address in use for the next link.

## Problems and Troubleshooting

The separation of ARP, IPv4 and ICMP was the biggest difficulty. Considering the captured frame as a stack of protocol layers simplified the understanding of the process. Finally, I concentrated on the different packet types than looking at each case where an Echo Request and an Echo Reply were both generated as separate events.

## Weekly Reflection

Week 4 took me from looking at network traffic and asking “why is this the case?” to deepening my understanding of the why. Switched LAN activity reinforced how End Devices and Intermediary Devices collaborate in order to enable communication between hosts, as well as how addressing and encapsulation are important for communication between hosts.

The most useful aspect of the week was laying these concepts of ARP in relation to the ICMP ping exchange. I discovered that before a host can send IP packets over Ethernet, it would first need to find out the MAC address of the next hop. I also became more comfortable with looking at the Ethernet, IPv4 and ICMP layers separately but knowing that they are all related and part of the same communication process.