## Computer Security

<h3>Chapter 1 Fundamental Concepts</h3>
<h4>1.1 Confidentiality, Integrity, and Availability </h4>

**C.I.A**
 -  **Confidentiality**
     - Avoidance of the unautorized disclosure of information 
        - Protection of data 
        - Providing access for those who are allowed to see it
      - *Encryption:*
        - transformation of info using an encryption key, so the encryted data can only be read using the decryption key.
        - secure -> encryption key difficult so someone cannot read cipher text with decryption
      - *Access control:*
        - policies that limit access to confidential information to systems with a 'need to know'
        - done by identity, name ,serial number, role of person 
      - *Authentication:*
        - the determination of the identity or role that someone has
        - by a key fob, smart card, password 
        - something you are, have or know 
      - *Authorization:*
        - the determindation if a person or system is allowed to access resources, based on acess control policy
      - *Physical Security:*
        - physical barriers to limit access to protected computational resources
        - locks on cabinets and doors
 -  **Integrity**
    - Property that information has not be altered in an unauthorized way
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
     - Need to protect metedata -> attributes of the file & info about access which aren't part of the content
       - time stamps, groups accessed, users
 -  **Availability**
    - Property that info is accessible and modifiable in a fashion by those authorized to do so
    - *Physical Protections:*
      - infrastructure meant to keep info available even in the event of physical challenge
      - building housing, systems to withstand storms, earthquakes & bomb blasts
    - *Computational redundancies:*
      - computer and storage devices that serve as fallbacks in case of failures 
      - redunduant arrays of inexpensive disks (RAID) use storage redundancies to keep data available to clients
    
      
<h3>Chapter 5  Network Security</h3>
<h4>1 Network Security Concepts</h4>
<h5>1.1 Network Topology </h5>

 - data packet is a finite-length set of bits -> divided into a 
   - header: specifices where the packer is going and contains various overhead/bookkeeping details
   - payload: actual information that is being communicated
- network connection structure  -> network topology
- computers in a network are **host nodes** that can be sources and destinations of messages
- routers are communcation nodes -> messages flow 
- physical connection between nodes define channels where messages travel so that packets move by being passed from one to another to get source -> destination
- private network of computers in close zone ->  *local area network (LAN)* 
  - internet -> *wide area network (WAN)* 
    - Antonomous Systems(ASs) -> wide area networks on the internet -> clusters
      - controlled by single organisation entity -> how packets are routed aong nodes
      - using shortest paths so distance is minimized and routing cycles are avoided
      - between ASs -> by contractual agreements, avoid loops 
      
<h5>1.1 Network Topology </h5>
