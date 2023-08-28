# Internet Protocol

### OSI Model

* Layer 7: Application
* Layer 6: Presentation
* Layer 5: Session
* Layer 4: Transport Layer
  * TCP / UDP / DCCP / SCTP / RSVP / QUIC
* Layer 3: Network - IP / Internet Layer -
  * IP, ICMP, NDP, ECN, IGMP,&#x20;
  * IP Packet - (Source IP + Destination IP + IP Data)
* Layer 2: Data Link&#x20;
* Layer 1: Physical Layer



### Network & Host

* `a.b.c.d/x` - x is the network bits and remains are host
* Example 192.168.254.0/24
  * The first 24 bits (3 byte) are network, the rest 8 are hosts
  * So - 2^24 - networks
  * each network has 2^8 hosts (255)&#x20;
* `192.168.254.0/24` is also called a subnet
  * **Subnet Mask:** The subnet has  a mask - 255.255.255.0
* **Default Gateway**
  * Most networks consists of hosts and default gateway
  * Two hosts can communicate directly, if they are in teh same subnet.
  * Each gateway has an IP address and host know its gateway. They communicate to other hosts which are not in the same subnet via the gateway.
  * Gateway is connected to multiple network and has multiple IP address - one for each network.

#### IP Packet

* Has headers and data sections
  * Headers - 20byte, can be upto 60 bytes if options are enabled
  * Data section can go upto 65536 (2^16) - 65KBs
  * average MTU (Maximum Transmission Unit) is 1500, so generally&#x20;
* Headers
  * Version (4)
  * IHL (4) - Internet Header Length
  * DSCP (6) -&#x20;
  * ECN (2)-&#x20;
    * When a routers' buffer is about to fill, it will set ECN
    * The receiver receives it and in the next pcaket it will send with ECN set to to true, so client and server eventually both knows, they are experience congestion
  * Total length (16 bit) - hence max can be 2^16
  * Identification
  * Flags
  * Fragment Offset
  * Time to live
    * Sender sends a counter (no. of hops) in which it can reach
    * All intermediate routers, would decrement by one and send it forward.
    * When its zero, the router will stop forwarding it and send an ICMP message
  * Protocol
  * Header Checksum
  * Source IP Address
  * Destination IP Address
  * Options (if HL > 5)
  * Data

#### ICMP - Internet Control Message Protocol

* Layer 3 protocol
* Designed for informational messages
  * Host unreachable, port unreachable, fragmentation needed
  * Packet expired (infinite loop in routers) - TTL
* Uses IP directly
* PING and traceroute uses it.
* Doesn't require listeners or ports to be opened.
* TCP Blackhole - when ICMP is blocked but your packet needed fragemenation. The router&#x20;



### UDP - User Datagram Protocol

* Layer 4 protocol
* Ability to address processes in a host using ports.
* 8 byte header Datagram
* UDP is stateless and no prior communication is required.
* Usecases
  * Video streaming
  * VPN (Generally&#x20;
  * DNS
  * WebRTC
* Headers
  * Source port
  * Destination port
  * Length
  * Checksum
* Pros
  * as
* Cons

#### Multiplexing & Demultiplexing

* Host runs many apps on different ports
* Sender multiplexes all its apps into UDP
* Receiver demultiplex UDP datagram to each apps.
