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
