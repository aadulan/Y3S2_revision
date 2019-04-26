## Computer Security

<h3>Chapter 1 Fundamental Concepts</h3>
<h4>1.1 Confidentiality, Integrity, and Availability </h4>

**C.I.A**
 -  **Confidentiality**
     - Avoidance of the unauthorised disclosure of information
        - Protection of data
        - Providing access for those who are allowed to see it
      - *Encryption:*
        - transformation of info using an encryption key, so the encrypted data can only be read using the decryption key.
        - secure -> encryption key difficult so someone cannot read cipher text with decryption
      - *Access control:*
        - policies that limit access to confidential information to systems with a 'need to know'
        - done by identity, name ,serial number, role of person
      - *Authentication:*
        - the determination of the identity or role that someone has
        - by a key fob, smart card, password
        - something you are, have or know
      - *Authorization:*
        - the determination if a person or system is allowed to access resources, based on access control policy
      - *Physical Security:*
        - physical barriers to limit access to protected computational resources
        - locks on cabinets and doors
 -  **Integrity**
    - Property that information has not be altered in an unauthorised way
    - *Backups:*
      - the periodic archiving of data
      - data files can be restored if altered in an unintended way
    - *Checksums:*
      - computation of a function that maps the contents of a file to a numerical value
      - depends on contents of file, a tiny change can result in a different value
      - used to detect a breach of data integrity
     - *Data correcting codes:*
        - method for storing data in a way that small changes can be easily detected and automatically corrected.
        - applied to small units of storage
     - All tools use redundancy -> replication of some content or functions
     - Need to protect metadata -> attributes of the file & info about access which aren't part of the content
       - time stamps, groups accessed, users
 -  **Availability**
    - Property that info is accessible and modifiable in a fashion by those authorised to do so
    - *Physical Protections:*
      - infrastructure meant to keep info available even in the event of physical challenge
      - building housing, systems to withstand storms, earthquakes & bomb blasts
    - *Computational redundancies:*
      - computer and storage devices that serve as fallbacks in case of failures
      - redundant arrays of inexpensive disks (RAID) use storage redundancies to keep data available to clients


<h3>Chapter 5  Network Security</h3>
<h4>1 Network Security Concepts</h4>
<h5>1.1 Network Topology </h5>

 - data packet is a finite-length set of bits -> divided into a
   - header: specifics where the packer is going and contains various overhead/bookkeeping details
   - payload: actual information that is being communicated
- network connection structure  -> network topology
- computers in a network are **host nodes** that can be sources and destinations of messages
- routers are communication nodes -> messages flow
- physical connection between nodes define channels where messages travel so that packets move by being passed from one to another to get source -> destination
- private network of computers in close zone ->  *local area network (LAN)*
  - internet -> *wide area network (WAN)*
    - Autonomous Systems(ASs) -> wide area networks on the internet -> clusters
      - controlled by single organisation entity -> how packets are routed among nodes
      - using shortest paths so distance is minimised and routing cycles are avoided
      - between ASs -> by contractual agreements, avoid loops

<h5>1.2 Internet Protocol Layers</h5>

- ***Internet protocol Stack***
    - layers provides a set of services & functionality guarantees for higher layers
    - interface each layer provides to higher levels -> provide essential info, lower level details are hidden
- ***Physical Layer:***
    - move the actual bits between nodes of the network
    - physical wires (abstraction it provides to the higher level is the ability)
- ***Link layer:***
    - transfer data between a pair of network nodes | between nodes in a local-area network and to detect errors that occur at the physical layer
    - deals with logic in sending info & how to find good routing paths in a local-area network.
    - Protocols such as Ethernet -> route packets between computers sharing a common connection
    - The link layer provides a grouping of bits into ordered records, called frames -> 48 bit address called *media access control addresses (MAC address)*
- ***Network layer:***
    - known as the internet layer
    - provide for moving of packets between any two hosts(best effort basis)
    - individually addressing each host using a *IP address*
    - Main protocol is (IP) -> IPv4(32 bit IP addresses), IPv6(128 bit IP address)
    - *Best Effort Basis*  no guarantees that any packet will be delivered, if reliable delivery is needed -> upper layer requirement
- ***Transport Layer:***
    - support communication and connections between applications based on IP address and ports(16 bit address) for application level protocols
    - *Transmission Control Protocol(TCP)*
        - virtual connection between a client and a server and guarantees delivery of all packets in an ordered fashion
    - *User Datagram Protocol(UDP)*
        - assumes no setup and delivers packets as quickly as possible but with no delivery guarantees
- ***Application Layer:***
  - protocols that support useful functions on the internet, based on the transport layer services.
  - HTTP -> uses TCP & supports web browsing
  - DNS -> UDP & supports use of useful names for hosts instead of IP address
  - SMTP & IMAP -> TCP & support electronic mail
  - SSL -> TCP & supports encrypted connections
  - VoIP -> UDP & supports Internet telephone messaging
- ***Open Systems Interconnection (OSI)***
    - seven layers
    - Application layer ->
        - Strict application layer -> host applications-to-network processes
        - presentation layer for inter-host communication
- Packet for a layer -> data transmitted + metadata providing routing & control info
    -  metadata stored -> header & sometimes footer
    - data portion -> payload
    - payload storing a packet is known as -> *encapsulation*
- ***Internet Protocol Stack***
    - functions and abstractions -> internet
    - layered model uses Internet Protocol Suite -> build software which uses approx services & provides right service guarantees  without ruining implementation details

<h5>1.3 Network Security Issues</h5>

- ***Confidentiality***
    - encryption could be done at application layer (https protocols & IP sec specs)
- ***Integrity***
    - checksums to validate a small number of bits not encryption -> not cryptographically secure.
    -  should be done at the application layers | alternative protocols at lower Layers
- ***Availability***
    - become unavailable -> lots of data requests,
    - need to scale with ↑ communications requests & block attacks from illegitimate request
-  ***Assurance***
    - by default, a packet is allowed to travel between any source and destination in a network, introduce permissions & policies that control data flow in a network, implemented as explicit additions, firewalls designed to blocked traffic in and out of a network domain, if that traffic violates policies set by the administrators
- ***Authenticity***
    - headers & footers -> internet protocol don't have a place to put digital signatures, no notion of user identities, data exchanged between machines & allow for signatures, explicitly at the application layer & alternative protocol
- ***Anonymity***
    - no default notion of identity of users of internet -> built-in anonymity -> good for human rights worker reporting on abuses & bad if thief steals credit card numbers identity

<h4>The Link Layer</h4>

- modern operating systems include TCP & IP implementation, allow programs to interact with IP stack
- libraries support upper levels (including passing data to physical layer device drivers)-> starts with the link layer ↑ above the physical layer & concept of group sequences of bits into frames

<h5>2.1 Ethernet</h4>

- Ethernet refers to physical medium (cable) as well as the link-layer protocol
- frame transmitted on a cable -> impulse is sent through cable & received by other machines that connect to cable on same *local-area network (LAN)*
- portion of local-area network -> same logical connection : *network segment*
- two machines on same network segment transmit a frame at same time, a collision occurs & frames must be discarded and retransmitted.
- ***Dealing with Collisions***
    - The Ethernet protocol is designed so that eventually every machine in a network segment will succeed in transmitting its frame.
- ***Ethernet Hub and switches***
    - a device that logically connects multiple devices together, allowing them to act as a single network segment (particpate in Ethernet Collision resolution protocol), can generate large amounts of traffic
    - Switches act like hubs but overtime learns the address of machines that are connected. a switch will then only forward each frame it receives along the cable it knows is connected to the destination for that frame.
    - reduces possibilties collisions & increases speed of network, effective bandwidth
    - reduces risk of network eavsdropping as network frames forwarded by a switch are less likely to been seen by machines which are not destinations

<h5>Media Access Control (MAC) Addresses </h4>

- network interfaces are typically identified by a hardware-specific identifier known as its media access control address (MAC address)
- 48 bit identifier assigned to a network interface by its manufacturer
- sequence of six pairs of hexadecimal digits 00:16:B7:29:E4:7D
- used in the link layer to indentify devices in a network - intended to be unique
- first 24 bits are a prefix identity the organisation
- can be changed by software through driver of network
- change -> the second-least-significant bit of the most significant byte is set to 1, while in a manufacturer-issued MAC, this bit is set to 0
- faciliate routing of frames to correct destinations
- what switches use
- format of a ethernet frame:
    - preamble
    - delimiter
    - mac dest/src
    - ethertype length
    - payload
    - CRc-32 checksum ->confirm data integegrity
    - interframe gap

<h5>ARP Spoofing</h4>

- The Address Resolution Protocol (ARP) is a link-layer protocol that pro- vides services to the network layer. ARP is used to find a host’s hardware address given its network layer address.
- Used to determine the mac adrress associated with a give IP -> valuable service (man in the middle attack agaisnt protocol)

<h6> How ARP works ? </h6>
- let a machine want to send a packet to a dest machine on the same network.
- at network layer - scr knows the dest ip address, sending the packet is job of the link layer, src needs to idenify the mac address of dest machine
- in arp proctol, resoulution of ip address to mac is done by a broadcast message that queries all network interfaces on a local-are network so proper destination can respond.
- the reply is transmitted in a frame addressed to the machine that made the  request.
- stored the IP-MAC address pair in a table called arp cache so doesn't have to do it again, src can send to dest
- lacks Authentication. Any computer on network could claim to request the ip address , any machine can recieve an arp reply even if it didn't make the request will automatically update the cache. Shortcoming, it is possible for malicious parties on a LAN to perform a arp spoofing attack,
- The attacker sned a arp reply to a target, who associates the ip address of the lan gateway with the attackers mac address. the atttacker sends an arp reply to bob associating the target ip's address with the attacker's mac address.this is arp cache poisioning. Bob now things alice ip is connected with eve mac  and alice thinks bob ip is connected to eve mac. thus everything is routed through eve.
- Eve now has control of traffic and can sniff passwords or tamper with traffic.
- a denial of service attack is also possible.
- arp spoofing is derived from lack of identity veriffication
- to solve :
    - restrict LAN Access
    - checking for multiple occurrences of the same MAC address on the LAN, which may be an indicator of possible ARP spoofing.
    - Static ARP Tables :
        - requires a network administrator to manually specify a router’s ARP cache to assign certain MAC addresses to specific IP addresses.
        - requests to adjust the cache are ignored
        - reduces flexibility if a new device joins
        - does not prevent an attacker from spoofing a mac address to intercept traffic

<h4>3 Network Layer </h4>
Network layer move packets between any two hosts in a network on a best effort basis. Relies on the link layer to do this.

<h5> IP </h5>
- The *Internet Protocol* (IP) is a protcol which performs a best efford to route a data packet from a src node to a dest node.
- In IP, every node is given a unique numerical address:
    -  32 bit number(IPv4)
    -  128 bit number (IPv6)

<h6> Routing IP Packets </h6>
A host has an algorithm for routing packets from that host:
    - Packet is addressed to a machine on the same LAN, then packet is transmitted directly on LAN using ARP to determine mac address of dest machine.
    - packet is address to a machine that is not on the LAN, packet is transmitted to a specially designated machine on LAN(gateway). ARP protocol is used to determine mac address of gateway
A host typically stores a list of IP address of the machines on LAN and the ip address of the gateway.
Once a packet has reached a gateway node, needs to be further routed to its final dest
Gateways and other nodes that handle routing of packets on the internet are called routers. Typically connected to two of more LANSs and use internal data structures known as routing tables to work out the next router.
data packet with dest t, a routing table lets the router determine which neighnour it should send the packet to. Based on the numerical address,t, the routing protocol encodes the next hop from this router to each possible destination.
There can be a misconfiguration in the routing tables that can cause a packet to travel forever. To stop this each IP packet is given (TTL - time-to-live) count by its scr. Known as a hop limit <= 255 hops and is decremented by each router that processes the packet.  if it =0 then packet is discared and error packet is sent to scr.

<h6> The structure of the internet </h6>
Routers are designed to be very fast. From each packet - it performs :
- ***Drop*** : if packet is expired,it is dropped
- ***Deliver*** : If the destination is a machine on one of the LANs to which
the router is connected, then the packet is delivered to the destination.
- ***Forward*** : If the destination of the packet does not belong to the LANs of the router, then the packet is forwarded to a neighboring router.

2 protocols that determine how the next hops are encoded:
- ***Open Shortest Path First (OSPF)*** : determines how packets are routed within an Autonomous system and is based on a policy that packets should travel along the shortest paths
- ***Border Gateway Protocol (BGP)*** : etermines how packets are routed between autonomous systems (ASs) and it is based on policies dictated by contractual agreements between different ASs The routes established by BGP may not be shortest paths.

Difference between a router and a switch is that a switch handles forwarding of packets on a single network and uses learned associations to reduce use of broadcasting . Router can belong to many networks and use routing tables to determine how to forward packets, can aviod broadcast altogether.

Bits in IP packet have a stucture
- fixed length header
    - total length of packet
    - TTL time to live
    - scr ip
    - dest ip
- variable length data portion

not guarantee that each packet successfully travels from its src to its dest, Ip can detect a packet headers are damaged. Comes with a checksum value, host or router can check -> need to recompute the function and compare value.the time-to-live, are modified with each hop, this checksum value must be checked and recomputed by each router that processes this packet.

Subnetworks (subnets) allow partitions in the networks into logical groups.IPv4  32-bit numbers that are stored as binary but written as 4 bytes
- network portion -> ip prefix used by all machines on the same network
- a host portion -> detect that particular device
- two portions are differentiated by providing a subnet mask along with the IP address.
- The network portion of the IP address can be identified by bitwise ANDing the subnet mask with the IP address, and the host portion can be identified by XORing this result with the IP address.
- subnet masks can be used to define address range of a particular network
- range of ip addtess are based on size of organization in question.
    - ***Class A*** network : largest, has a subnet mask of at least 8 bits and includes up to 224 = 16, 777, 216 unique IP addresses
    - ***Class B*** network : have at least a 16-bit subnet mask and up to 216 = 65, 536 unique IP addresses; they are typically allocated for ISPs and large businesses.
    - ***Class C*** network : 4-bit subnet mask, include up to 28 = 256 unique addresses, and are assigned to smaller organizations.
IP addresses with the host portion consisting of all zeros or all ones have a special meaning and are not used for to identify machines. Thus, a class C network has 254 usable IP addresses. Total address space for IPv4 is on the verge of exhaustion: soon, all possible IPv4 addresses will be assigned. Network Address Translation, or NAT delays the exhaustion of the IPv4 address space, it doesn’t solve it, and an actual solution is provided by IPv6, which features 128-bit addresses.

<h6> Internet Control Message Protocol</h6>
- Network layer protocol (ICMP)
- used by hosts to perform a number of testing and error notfi tasks.
- network diagnostic tasks
- determining if a host is alive & finding the path followed by a packet:
    - ***Echo request*** : Asks the destination machine to acknowledge the re- ceipt of the packet
    - ***Echo response*** : Acknowledges the receipt of a packet in reply to an echo request
    - ***Time exceeded*** : Error notification that a packet has expired, that is, its TTL is zero
    - ***Destination unreachable*** : Error notification that the packet could not be delivered

- ***Ping*** :uses the ICMP protcol to verify whether or not a certain host is receiving packets. ICMP echo request message to the dest host, replies with an ICMP echo response message. Simple protocol is often the first diag- nosis tool used to test if hosts are working properly.
- ***Traceroute*** : ICMP messages to determine the path a packet takes to reach another host, either on a local network or on the Internet.  It uses TTL field in the IP header. Attempts to send a packet to the target with a TTL. Receiving a packet with TTL of 1, intermediate router discards the packets and replies to the sender with an ICMP time excceeded message,revealing the first machine along the path to the target.. it sends another packet with a TTL of 2, reaching the first router in the path, the TTL is decremented by one and forwarded to the next router. in turn sends an ICMP packet to the original sender, incrementing the TTL field in this way, traceroute can determine each host along the path to the target

<h6> IP Spoofing</h6>
IP packet includes a place to specify the IP addresses of the destination and source nodes of the packet.
validity of the source address is never checked, it is trivial for anyone to specify a source address that is different from their actual IP address. Nearly every operating system provides an interface by which it can make network connections with arb ip header info so it can make connections. spoofing is specifing the desired ip is scr filed of an ip packet data before sending it to network.
IP spoofing does not let an attacker assume an new ip by changed headers, the ip stays the same

<h6> How IP Spoofing is used in other attacks</h6>
attacker sends an IP packet with a spoofed src address, won't receive a repsonse from dest server. spoofed src ip address on an outbound packet, machine with the server spoofed ip address will receive a response from the dest server not the attacker.
attacker is using IP spoofing on his outbound packets, must not car about any response for these packets or has a way to receive response

<h6> Dealing with IP Spoofing</h6>
- Border Routes: routers span two or more subnetworks can be used to block packets from outside their admin domain that have scr address from inside domain
- IP traceback : tracing path of a packet back to its actual src address. Requests can be made to various autonomous systems along this path to block packets from this location

<h5> Packet Sniffing </h5>
Comprising confidentiality. Possible to listen in on the traffic . Known as packet sniffing.
Performed independlty of wheather the packets are traveling via wireless Internet : attacker resides on the same network segment
Frames are transmitted over an ethernet network, received by ever device on same network.
segment will normally compare the frame’s destination MAC address with its own MAC address, and discard the frame if it doesn’t match.
Network mode set to *promiscuous* mode, llows an attacker to examine all data transmitted over a particular network segment

<h6> Defenses against Packet sniffing</h6>
- PS can be used to troubleshoot network related problems -> computer is infected with adware or spyware
- Use Ethernet switches instead of Hubs, less number of machines on attacker network segment,Note that there is no analog to the switch when communicating wirelessly,
- detect when network devices are in promiscuous mode
    - the fact that when a network interface is receiving all network traffic, the operating system behind that network interface is using much more processing power than if these frames were being dropped
    - elicit responses to invalid packets from network devices may provide clues suggesting
    - should use encryption HTTPS instead of HTTP

<h4>4 Transport Layer </h4>
supports communication between machines.addressing extended is achieved by viewing each machine as having lots of ports.
16-bit source and destination port numbers.
Protocols:
- Transmission Control Protocol (TCP)
- User Datagram Protocol (UDP)
Extra feature of tcp connection oriented and provides reliable stream of bytes, with a gurantee that info arrives intact. if lost it is resend
UDP best-effort communicatiin : where speed is more important than completeness.


<h5>Transmission Control Protocol (TCP)</h5>
Takes IP Protocol and gurantees transmission of a stream of bits between two virtual ports.

<h6>Transmission Control Protocol (TCP)</h6>
TCP session starts with connection between sender & receiver, parties can then communicate. Ensures reliable transmission by a sequence number that is initalised during the three-way handshake, Transmission features an incremented sequence number, each part is aware when packets arrive, out of order all or not at all,
Incoporates a cumulative acknowledge schemem two TCP sessions , sender and receiver communicating via their established TCP connection.
the sender sends the receiver a specified amount of data, the receiver will confirm that it has received the data by sending a response packet to the sender with the acknowledgment field set to the next sequence number it expects to receive. If any information has been lost, then the sender will retransmit it.
Manages amount of data that can be sent by one party while avioding overwhleming, processing resources of other or bandwidth of network itself(*flow control*) use *sliding window protocol* -> receiver informs sender of size of receive window(number of bytes of data willing to accept befor sender must pause and wait for a response), sender keeps track of value of last thing.  When sending , the sender checks the sequence number of packet and continues only if number is less than last acknowedlenge plus current size of recevive window. Otherwise it waits, stores the number shifting sliding window of sequence numbers. Sender sets a time so if no acknowledgment is received before the times expires, sender assumes data loss and retransmits
Checksum field to ensure correctness. not intended to be cryptographically secure, detect inconsistencies in data due to network erros rather than tamoering.

<h6>Congenstion Control</h6>
attempt to prevent overwhelming a network with traffic which could lead in poor transmission rates and dropped packets. congenstion control is not implemented into tcp packets but based on the info gathered by keeping track of acknowledgements for prev sent data and time required for certain operations. TCP adjusts data transmission rates using this information to prevent network congestion.

<h6>TCP Packet Format</h6>
Format of TCP :
- dest port
- scr port
- communication connection for this packet and others like it
- connections have a state

<h6>TCP Connections</h6>
- three-way handshake to establish a reliable connection stream between 2 parties, client sends packef to desired dest with SYN(synchronization) flag, included a random initialization for *sequence numbers*, used for reliable ordering of future transmissions. SErver replies with a packet marked with SYN and ACK(acknowledgement) flags (SYN-ACK) packet, says servers wants to accept. set with an acknowledgement no(set to more than 1 of sequence number and new random seq num) client responds with ACK packet to say successful connect, Final ACK packet features an acknowledgment number ( set to one more than the most recently received sequence number, and the sequence number set to the recently received acknowledgment number.)

16 bit port num differenitate multiple TCP connections. packets include src port and dest port. orts may range from 1 to 65,535 (216 − 1), with lower port numbers being reserved for commonly used protocols and services.
port 80 - HTTP
port 21/22 - FTP , SSH
applications can create network connections using sockets

<h5>User Data Protocol (UDP)</h5>

- UDP doesn't make a gurantee about the order /correctness of packet delivery. No inital handshake to establish connection, allows to send messages (datagrams) asap. if sender wants to communicate via UDP, it only needs a socket.
- UDP features a 16 bit checksum to verfiy the inegrity og each packet, no seq num scheme, so transmissions can arrive out of order or may not arrive at all. Assumed that checking for missing packets is left to application. UCP can be faster than TCP
- Often used in time-senstive applications where data integrity is not as important as speed(DNS or VoIP) TCP is used for applications where order and intergirty matter (HTTP,SSH,FTP)
- Header :
    - Src port
    - dest port
    - length
    - checksum
- Payload
    - Data

<h5>Network Address Translation(NAT)</h5>
- add network devices to home network, typically don't buy ip address and set up the new address directly on the Internet.
- *Network address Translation* : allows machines on local-area network to share a single public IP address. Public IP add represents the point of contact with internet for entire LAN, while machines on network have private IP add that only accessible from within network
- NAT allows an entire network to be asssigned to a single public IP add, widespread use of NAT, delayed inevitable exhaustion of the IPv4 space,
a lot of address capacity for NAT, because there are a number of private IP addresses that such networks are allowed to use which cannot be used on the (public) Internet.
- e IP address are of the form 192.168.x.x, 172.16.x.x through 172.31.x.x, and 10.x.x.x.
- NAT router represents the gate- way between private IP addresses and the public Internet, and this router is responsible for managing both inbound and outbound Internet traffic.

<h6>How NAT Works?</h6>
- translate by a look up table-> contains entries:
    - private scr IP
    - private scr port
    - dest ip
    - public src port
- dynamically rewrite headers of all inbound and outbound tcp and udp packets,
- machine on internal network attempts to send a packet to an external IP address, the NAT router creates a new entry in the look up table associated with the src machine private ip add, & internal src port of transmitted packet,rewrites the scr ip to be that of NAT device public ip , opens a new public src port, rewrites ip header src port field contain newly opened port. public port and dest ip are recorded with private src ip and private internal port in NAT lookup table. device also adjusts any checksum contained in packet, including used by ip, tcp&udp to reflect changes made, packet is forwared to dest.
- NAT router check look up table for any entries whose public scr port corresponds to dest port of inbound packet & dest ip address corresponds to src ip on inbound packer. NAT router rewrites ip headers of inbound packet in line with lookup table, packet is forwared to correct private ip add and private port
- effecrivley manages outbound traffic, several restrictions on inbound traffic, external machine has no way to start a connection with machine on provate network, since internal m doesn't have a oublicy accessible IP address, can be a security feature since no inbound traffic from internet can reach internal network, NAT devices can function as firewalls, blocking risky contact from the external internet
- violates the ideal goal of end-to-end connectivity for machines on internet by not allowing direct communication between internal and external parties, NAT can cause problems with protcols, if not tcp or udp as a transport layer protocol, cruical in delaying exhaustion of IPv4 address space and simplifying home networking

<h5>TCP Session Hijacking</h5>

<h6>TCP Sequence Prediction</h6>
- *Session Spoofing* creates a spoofed TCP session instead of stealing an existing one, type of session hijacking, *TCP sequence prediction* attack triws to guess the inital sequence number sent by the sercer at start of a session. Early TCP stacks implemented sequence numbers by using a simple counter that was added 1 with each transmission.Not using any randomness, trival to predict next sequence number, key to attack. Modern TCP stack implementations use pseudo-random numbers generators to determine seqence numbers, makes TCP sequence prediction attack more difficult, not impossible. Following scenarios could happen:
1. The attacker launches a denial-of-service attack against the client victim to prevent that client from interfering with the attack.
2. The attacker sends a SYN packet to the target server, spoofing the source IP address to be that of the client victim.
3. After waiting a short period of time for the server to send a reply to the client (which is not visible to the attacker and is not acted on by the client due to the DOS attack), the attacker concludes the TCP handshake by sending an ACK packet with the sequence number set to a prediction of the next expected number (based on information gathered by other means), again spoofing the source IP to be that of the client victim.
4. The attacker can now send requests to the server as if he is the client victim.

<h6>Blind Injection</h6>
above attack only allows one-way communication as attacker cannot receive any replies from the server due to use of the IP spoofing. method may allow an attacker to subvert a system that excutes a certain command based on scr of IP of requester.possible to inject a packet containing a command that creates a connection back to the attacker.


<h6>ACK Storms</h6>
possible side effect of blind injection attack, is that can cause a client and server to become out-of-synchronization with respect to a sequence numbers, as server got a synchronized message, client never actually sent. TCP incopoartes a method for clients & servers to become resynchronized when they go out of step, but it doesn't easy tolerate desyncronization that happens after a blind injection attack. Server and client start sending ACK messages to start using correct sequence numbers, known as ACK Storm, can continue until one of these messages is lost by an accident or a firewall detects an ack storm in progress and discards a bad ack message.

<h6>Complete Session Hijacking</h6>
attacker on same network segment as target server, and or client, attacker can hijack an tcp session. possible due to packet sniffing to see sequence numbers of packets used to establish session. attacker can inject a packer with high probable sequence number to server useing a spoofed src ip address to be like the client. Used in combination with other network attacks, possibility of an attacker who is in same network segment as target server or client victim allows for an even stronger type of session hijacking attack. an attacker on same network segment as client or server can use packet sniffing to see sequence numbers of packets used to establish a tcp session as in a complete session stealing attack, but he can also sometimes go a step further by creating a man-in-the-middle attack using ARP spoofing method. Once done attacker can perform all subsequent actions as if he were the user, masquerading as, he can intercept all responses from both sides.

<h6>Countermeasures</h6>
- use encryption & authentication, at network layer suce as IPsec or application layer
- web sites avoid creating sessions that begin with secure authentication measures but subsequently switch over to unencryted exchanges.
- trade fair efficiency for security, create a risk with respect a tcp session hijacking attack.

<h4>Denial-of-Service Attacks</h4>
Bandwidth in a network is finite, number of connections of a web server can maintain to clients is limited. connection to a server needs a minimum amount of network capacity to function. A server has used up its bandwidth or ability of its processors to respond to Requests, additional attempted connections are dropped & potential clients will be unable to access resources provided by server. attacl that is designed to cause a machine or piece of software to be unavailable and unable to perform its basic functionality is known as a denial-of- service (DOS) attack.

Not concerned with receiving responses from a target, spoofing src ip address is commonly used to obscure the identity of the attacker as well as make mitigation of attack more difficult. Servers can stop DOS attacks by dropping all packets from certain blacklisted ip address, attackers can generate a unique src ip address for every packet sent, preventing target from successfully identifying & blocking attacker. IP spoofing can make it more difficult to target the src of a dos attack.

<h5>ICMP Attacks</h5>
<h6>The Ping Flood Attack</h6>
- Ping utility sends an ICMP echo reuqest to a host, returns with ICMP echo reponse.
- powerful machine sends massive amounts of echo requests to a single victim server
- attacker can create more ping requests than victim can process & victim has enough network bandwidth to receive all these requests, victim server will be overwhelmed with traffic & start to drop legitimate connections

<h6>The Smurf Attack</h6>
- takes advantage of misconfigured networks is known as a smurf attack
- networks feature a boradcast address - user can send packet that is received by every IP address on network.
- Smurf attacks exploit property by sending ICMP Packets with scr address set to target and with dest address set to broadcast address of network
- Each packet received by every machine on network at which point every machine sends a reply ICMP packet to indicated src address of target, results in am amplification effect that multiplies number of packets sent by number of machines on network.
- victmins many be on exploited network or traget, identity of attacker is further obscured
- to prevent
    - admin should configure hosts & routers on their networks to ignore broadcasts requests,
    - routers should be configures to avoid forwarding packets directed to broadcast address, poses a security risk in network can be used a ping flood amplifier, server is relatively weak, wise for it to ignore ping requests to avoid ping floods.

<h5>SYN Flood Attacks</h5>
to initiate TCP session ,client sends a SYN packet to a server, in response to which the server sends a SYN,ACK packet. This exchange is normally then followed by client sending a concluding ACK packet to server, client nevers sends the concluding ACKm server waits for a certain time out period then discards session.

<h6>SYN Flood Attacks</h6>
attacker sends a large number of SYN packets to server, ignores SYN/ACK replies, never sends expected ACK packets, attacker initaing attack in practice will use random spoofed src address un SYN packets he sends, so replies are sent to random ip address. attacker sends a large amount of SYN packets with no corresponding ACK packets, server's memory will fill up with sequence numbers that is is remebering in order to match up with TCP sessions with expected ACK packets, never arrive so wasted memory blocks out other legiti ate TCP session requests.

<h6>Defense Against SYN Flood Attacks</h6>
- *SYN Cookies* server sends a speical crafted SYN & ACK packet, without creating a corresponding memory entry
