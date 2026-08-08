# Week 2 Journal – Computer Networks and the Internet

**Student Name:** Yashwanth  
**GitHub:** https://github.com/yashwanth5050  
**Unit:** COIT20246 Networking and Cyber Security  
**Week:** 2  
**Topic:** Computer Networks and the Internet

## Activity 1 – Testing Network Connectivity with Ping

### Objective

The purpose of this activity was to observe the result of a network connectivity test using the `ping` utility. I examined the replies returned from the destination and used the final statistics to understand packet delivery and round-trip time.

### Work Completed

The Command Prompt screenshot shows repeated replies from the IP address `93.184.216.34`. Each visible reply contains `bytes=32`, a response time close to 101–106 ms, and `TTL=52`.

The final ping statistics show:

```text
Packets: Sent = 111, Received = 111, Lost = 0 (0% loss)
Minimum = 101ms
Maximum = 154ms
Average = 102ms
```

The test was stopped using `Ctrl+C` after 111 packets had been transmitted.

### Evidence

![Figure 2.1 – Ping test showing successful replies and zero packet loss](images/week02-ping-tests.png)

**Figure 2.1 explanation:** This screenshot shows successful replies from `93.184.216.34`. The final statistics report 111 packets sent, 111 packets received and 0% packet loss. The minimum round-trip time was 101 ms, the maximum was 154 ms and the average was 102 ms.

### Interpretation

The results show that the destination was reachable during the captured test because every transmitted packet received a reply. The 0% packet loss indicates that none of the 111 packets were lost during the test.

The response times also show the delay between sending the ping request and receiving the reply. Most visible replies are close to 102 ms, while the overall maximum recorded delay was 154 ms. The `TTL=52` value is included in the returned replies and represents the remaining Time To Live value of the received IP packet.

## Activity 2 – Examining ICMP Traffic in Wireshark

### Objective

The purpose of this activity was to examine ping traffic at packet level using Wireshark. This allowed me to see the relationship between ICMP Echo Request and Echo Reply packets and to inspect the protocol information associated with the captured traffic.

### Work Completed

I examined the packet capture shown in Wireshark. The capture contains ARP traffic followed by ICMP traffic between the hosts `192.168.1.11` and `192.168.2.21`.

The first visible ICMP packet is an Echo Request from:

```text
Source:      192.168.1.11
Destination: 192.168.2.21
Protocol:    ICMP
Length:      98 bytes
TTL:         64
```

The next packet is the corresponding Echo Reply from:

```text
Source:      192.168.2.21
Destination: 192.168.1.11
Protocol:    ICMP
Length:      98 bytes
TTL:         63
```

Several additional request-and-reply pairs are visible with increasing sequence numbers.

The screenshot also shows ARP packets such as:

```text
Who has 192.168.1.1? Tell 192.168.1.11
192.168.1.1 is at 08:00:27:e9:b4:2f
```

### Evidence

![Figure 2.2 – Wireshark capture showing ICMP Echo Request and Echo Reply packets](images/week02-wireshark-icmp.png)

**Figure 2.2 explanation:** This screenshot shows ICMP Echo Request packets travelling from `192.168.1.11` to `192.168.2.21` and Echo Reply packets returning from `192.168.2.21` to `192.168.1.11`. ARP packets are also visible at the beginning and later in the capture.

### Packet Inspection

The selected packet is an ICMP Echo Request. In the packet details pane, Wireshark displays several protocol layers:

```text
Frame
Ethernet II
Internet Protocol Version 4
Internet Control Message Protocol
```

The Ethernet II information for the selected frame shows the source MAC address as:

```text
08:00:27:ef:bf:5e
```

and the destination MAC address as:

```text
08:00:27:e9:b4:2f
```

The IPv4 section shows:

```text
Source IP:      192.168.1.11
Destination IP: 192.168.2.21
```

This demonstrates that Wireshark can show both link-layer Ethernet information and network-layer IPv4 information for the same packet.

### Interpretation

The repeated Echo Request and Echo Reply pairs provide packet-level evidence of communication between the two hosts. An Echo Request is sent by `192.168.1.11`, and a corresponding Echo Reply is returned by `192.168.2.21`.

The screenshot also helped me see that network communication is organised into layers. The same captured packet contains an Ethernet frame, an IPv4 packet and an ICMP message. Wireshark presents these layers separately so that each part of the communication can be inspected.

The ARP packets visible in the capture also demonstrate that address resolution is taking place on the local network. In the displayed exchange, a device asks for the physical address associated with `192.168.1.1`, and a response identifies the corresponding MAC address.

## Problems and Troubleshooting

I did not encounter a major failure in the ping test because the screenshot shows 0% packet loss. The main challenge was interpreting the large amount of information displayed in Wireshark.

I focused on the Source, Destination, Protocol and Info columns first, then used the packet details pane to distinguish the Ethernet II, IPv4 and ICMP sections. This made the packet capture easier to understand.

## Weekly Reflection

Week 2 helped me understand network connectivity at two different levels. The Command Prompt output gave me a simple summary of whether packets were successfully reaching a destination, while Wireshark showed the individual packets responsible for that communication.

The ping result was useful because it clearly showed successful communication with 0% packet loss and measurable round-trip times. The Wireshark capture then provided a deeper view by showing the ICMP Echo Requests and Echo Replies between two IP addresses.

The most useful part of this activity was seeing how a simple connectivity test is represented as actual network packets. I also learned that one packet can contain information from several protocol layers, including Ethernet, IPv4 and ICMP. This made the relationship between basic network testing and packet analysis much clearer to me.
