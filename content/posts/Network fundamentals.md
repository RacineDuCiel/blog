---
title: 'Network fundamentals'
date: 2024-04-21
tags: ["network"]
TocOpen: true
---

## Network Terms 

- **WAN (Wide Area Network):** 
  - Definition: The Internet; a large network connecting multiple LANs.
  - Identification: WAN-specific routing protocols like BGP and non-RFC 1918 IP schemas.
  
- **LAN (Local Area Network):**
  - Definition: Internal networks (e.g., home or office).
  - IP Addressing: Typically RFC 1918 addresses.
  
- **WLAN (Wireless Local Area Network):**
  - Definition: Wireless variant of LAN, enabling Wi-Fi access.
  - Security: Mainly a security designation; no fundamental difference from LAN.
  
- **VPN (Virtual Private Network):**
  - Goal: Allows users to feel connected to a different network securely.
  - Types: Site-to-Site, Remote Access, SSL VPN.
  

### VPN Types

- **Site-To-Site VPN:**
  - Devices Involved: Routers or Firewalls.
  - Function: Shares entire network ranges between client and server.
  
- **Remote Access (client to site) VPN:**
  - Function: Client's computer creates a virtual interface to the client's network.
  - Considerations: Split-Tunnel VPNs for selective routing.
  
- **SSL VPN:**
  - Function: VPN within a web browser, streaming applications or desktop sessions.
  - Example: HackTheBox Pwnbox.
  

### Book Terms

- **GAN (Global Area Network):**
  - Definition: Global network like the Internet; used by international companies.
  - Infrastructure: Utilizes WAN infrastructure and international connections.
  
- **MAN (Metropolitan Area Network):**
  - Definition: Regional network connecting multiple LANs in proximity.
  - Infrastructure: Utilizes high-performance routers and fiber connections.
  
- **PAN / WPAN (Personal Area Network / Wireless Personal Area Network):**
  - PAN Definition: Ad hoc network connecting devices via cable.
  - WPAN Definition: Wireless variant using Bluetooth or Wireless USB technologies.
  - IoT Application: Used for smart homes and home automation with protocols like ZigBee.


## Network topologies 

### Overview

- **Definition:** A network topology refers to the arrangement and connections of devices in a network, determining communication paths.
- **Physical Topology:** Concerns the physical layout of devices and cabling.
- **Logical Topology:** Concerns how data is transmitted across the network regardless of physical connections.

### Components

- **Connections:**
  - *Wired:* Coaxial, Glass fiber, Twisted-pair cabling, etc.
  - *Wireless:* Wi-Fi, Cellular, Satellite, etc.
- **Nodes:** Devices facilitating communication:
  - Repeaters, Hubs, Bridges, Switches, Routers/Modems, Gateways, Firewalls.
- **NICs (Network Interface Controllers):** Enable communication between nodes.

### Basic Topologies

1. **Point-to-Point:**
   - Direct connection between two hosts; basic telephony model.
   
2. **Bus:**
   - All hosts connected via shared transmission medium; one host can send at a time.

3. **Star:**
   - Central network component (router, hub, switch) connects to each host individually.

4. **Ring:**
   - Physical: Each node connects to the ring with separate cables for incoming and outgoing signals.
   - Logical: Stations access the ring sequentially using a token.

5. **Mesh:**
   - Fully Meshed: Every node is connected to every other node; high reliability and bandwidth.
   - Partially Meshed: Nodes connected with varying degrees of connectivity.

6. **Tree:**
   - Extended star topology; useful for larger networks or combining multiple topologies.

7. **Hybrid:**
   - Combination of two or more basic topologies; resulting network is non-standard.

8. **Daisy Chain:**
   - Nodes connected sequentially; often found in automation technology.


## Proxies Cheat Sheet

### Overview

- **Definition:** A proxy acts as a mediator between client and server, inspecting and potentially modifying traffic.
- **Misconceptions:** Often confused with VPNs; proxies typically operate at Layer 7 of the OSI Model.

### Types of Proxies

1. **Dedicated Proxy / Forward Proxy:**
   - Forward proxies filter outgoing requests from clients.
   - Example: Corporate networks use forward proxies for security, filtering, and monitoring.

2. **Reverse Proxy:**
   - Listens for incoming requests and forwards them to backend servers.
   - Example: Cloudflare serves as a reverse proxy to protect against DDoS attacks.

3. **(Non-) Transparent Proxy:**
   - **Transparent Proxy:** Operates without the client's knowledge, intercepting and substituting requests.
   - **Non-Transparent Proxy:** Requires client and software to be configured to use it explicitly.

### Use Cases

- **Security Professionals:** Utilize proxies for testing, analyzing, and intercepting network traffic (e.g., Burp Suite).
  
- **Web Developers:** Employ proxies like Cloudflare or ModSecurity for filtering and blocking malicious traffic.

- **Average Users:** Often mistakenly refer to VPNs as proxies for location obfuscation and accessing region-restricted content.
  
- **Law Enforcement:** May associate proxies with illegal activities due to their potential for anonymity and traffic manipulation.

### Examples

- **Forward Proxy Example:**
  - **Usage:** Filtering outbound requests in a corporate network.
  - **Tool:** Burp Suite, commonly used for HTTP request forwarding and analysis.

- **Reverse Proxy Example:**
  - **Usage:** Protecting servers from DDoS attacks.
  - **Tool:** Cloudflare, acting as a reverse proxy to filter and distribute incoming traffic.

- **Transparent Proxy Example:**
  - **Usage:** Intercepting and substituting client requests without their knowledge.
  - **Implementation:** Often employed in corporate environments for security and monitoring purposes.

![proxy](/images/proxy.png)

## OSI - TCP/IP models 

![net_models](/images/net_models_pdu2.png)

### Packet Transfers

- **Protocol Data Unit (PDU):**
    - **Definition:** Data format exchanged between layers in a layered system.
    
- **Encapsulation:**
    - **Process:** Each layer adds a header to the PDU from the upper layer, controlling and identifying the packet.
    
- **Transmission Process:**
    - Data is processed layer by layer, with each layer performing its assigned functions.
    - Header and data together form the PDU for the next layer, continuing until data reaches the receiver.


### OSI 

1. **Physical Layer (Layer 1):**
    - **Function:** Handles transmission techniques, such as electrical signals, optical signals, or electromagnetic waves.
2. **Data Link Layer (Layer 2):**
    - **Function:** Enables reliable and error-free transmissions by dividing bitstreams into blocks or frames.
3. **Network Layer (Layer 3):**
    - **Function:** Establishes connections in circuit-switched networks and forwards data packets in packet-switched networks.
4. **Transport Layer (Layer 4):**
    - **Function:** Provides end-to-end control of transferred data, detecting and avoiding congestion situations and segmenting data streams.
5. **Session Layer (Layer 5):**
    - **Function:** Controls logical connections between systems, preventing connection breakdowns or other issues.
6. **Presentation Layer (Layer 6):**
    - **Function:** Transfers system-dependent data presentations into a form independent of the application.
7. **Application Layer (Layer 7):**
    - **Function:** Controls input and output of data, providing application functions among other tasks.



### TCP/IP 

1. **Link Layer (Layer 1):**
    - **Function:** Places TCP/IP packets on the network medium and receives corresponding packets, independent of network access method or frame format.
2. **Internet Layer (Layer 2):**
    - **Function:** Handles host addressing, packaging, and routing functions to ensure data packet delivery to the intended destination.
3. **Transport Layer (Layer 3):**
    - **Function:** Provides TCP session and UDP datagram services for applications, controlling data transfer and ensuring connection between data stream and application.
4. **Application Layer (Layer 4):**
    - **Function:** Allows applications to access services from other layers and defines protocols for data exchange between applications.



### CIDR Notation

- **Classless Inter-Domain Routing (CIDR):** Offers a flexible method of IP address representation.
- **Format:** Combines the IP address with a slash followed by a number indicating the number of network prefix bits (e.g., 192.168.10.39/24).


## MAC Addresses

- **MAC Address:** A 48-bit (6 octets) unique identifier assigned to each network interface card (NIC) for communication on a network.
- **Representation:** Expressed in hexadecimal format, commonly separated by colons, hyphens, or periods.
- **Standards:** Used in Ethernet (IEEE 802.3), Bluetooth (IEEE 802.15), and WLAN (IEEE 802.11) networks.

### Structure

- **Format:** Consists of 6 pairs of hexadecimal digits (octets).
- **Organization:**
  - First 3 octets: Organization Unique Identifier (OUI) assigned to manufacturers by IEEE.
  - Last 3 octets: Individual Address Part, assigned by manufacturers.

### Types of MAC Addresses

- **Unicast:** Sent to a specific host, identified by the last bit of the first octet (0).
- **Multicast:** Sent to a group of hosts, identified by the last bit of the first octet (1).
- **Broadcast:** Sent to all hosts on the network, identified by all bits set to 1.

### Reserved MAC Address Ranges

1. **Local Range:**
    - **Definition:** This range is reserved for local use within a network and is not intended to be globally unique. Devices within a local network might generate MAC addresses within this range for internal communication.
    - **Examples:**
        - `02:00:00:00:00:00`: Often used for testing and debugging purposes.
        - `06:00:00:00:00:00`: Reserved for network interface cards with multicast capabilities.
        - `0A:00:00:00:00:00`: Used for Virtual Local Area Network (VLAN) tagging.
        - `0E:00:00:00:00:00`: Reserved for future use.

These reserved MAC address ranges help prevent conflicts and ensure that certain types of MAC addresses are not inadvertently assigned to devices on a network. They are primarily used for special networking functionalities and should not be used for regular network devices.

### MAC Address Manipulation

- **MAC Spoofing:** Altering a device's MAC address to impersonate another device, often used for unauthorized access.
- **MAC Flooding:** Sending numerous packets with different MAC addresses to overwhelm a network switch.
- **MAC Filtering:** Restricting network access based on approved MAC addresses, potentially exploitable with spoofed addresses.

### Address Resolution Protocol (ARP)

- **Purpose:** Maps IP addresses to MAC addresses for communication on a LAN.
- **Process:**
  - ARP Request: Device broadcasts request for MAC address corresponding to a given IP address.
  - ARP Reply: Device with matching IP address responds with its MAC address.
- **Vulnerabilities:** Can be exploited for attacks like ARP Spoofing, leading to interception or manipulation of network traffic.

### ARP Spoofing

- **Definition:** Sending falsified ARP messages to associate attacker's MAC address with target's IP address.
- **Goal:** Intercepting traffic intended for the target, facilitating various malicious activities.
- **Mitigation:** Implement secure network protocols, firewalls, and intrusion detection systems to protect against ARP spoofing attacks.


## IPv6 Addresses 

1. **Basic Information:**
   - IPv6 is the successor of IPv4, with a 128-bit address space.
   - IPv6 addresses are represented in hexadecimal format.
   - IPv6 follows the end-to-end principle, providing globally accessible IP addresses without the need for NAT.

2. **Address Types:**
   - **Unicast:** Addresses for a single interface.
   - **Anycast:** Addresses for multiple interfaces, with only one receiving the packet.
   - **Multicast:** Addresses for multiple interfaces, where all receive the same packet.
   - **Broadcast:** Does not exist in IPv6 and is replaced by multicast addresses.

3. **Hexadecimal System:**
   - Hexadecimal system (hex) is used to represent IPv6 addresses.
   - Hexadecimal characters range from 0 to F, corresponding to binary groups.
   - Simplifies representation compared to binary, making it more readable.

4. **Representation:**
   - IPv6 addresses are divided into 8 blocks of 16 bits each, separated by colons (:).
   - Leading zeros in each block are omitted.
   - Consecutive blocks of zeros can be represented as "::" once, starting from the left.

5. **Example:**
   - Full IPv6: `fe80:0000:0000:0000:dd80:b1a9:6687:2d3b/64`
   - Short IPv6: `fe80::dd80:b1a9:6687:2d3b/64`

6. **Address Structure:**
   - Consists of two parts: Network Prefix and Interface Identifier (Suffix).
   - Network Prefix identifies the network or subnet.
   - Interface Identifier is formed from the MAC address and converted to a 64-bit address.
   - Typical prefix lengths include /32, /48, /56, and /64.

7. **RFC 5952 Notation:**
   - All alphabetical characters are lowercase.
   - Leading zeros in each block are omitted.
   - Consecutive blocks of 4 zeros can be shortened with "::" once from the left.

8. **Advantages of IPv6:**
   - Larger address space.
   - Address self-configuration (SLAAC).
   - Multiple IPv6 addresses per interface.
   - Faster routing.
   - Mandatory support for IPsec.
   - Data packages up to 4 GB.

9. **Transition Mechanisms:**
   - Dual Stack: Simultaneous availability of both IPv4 and IPv6.
   - Tunneling: Encapsulation of IPv6 packets within IPv4 packets for transmission over IPv4 networks.

## Network Key Terminology

| **Protocol**                                      | **Acronym** | **Description**                                                                                                                                                                                                                                                                                |
| ------------------------------------------------- | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wired Equivalent Privacy                          | `WEP`       | WEP is a type of security protocol that was commonly used to secure wireless networks.                                                                                                                                                                                                         |
| Secure Shell                                      | `SSH`       | A secure network protocol used to log into and execute commands on a remote system                                                                                                                                                                                                             |
| File Transfer Protocol                            | `FTP`       | A network protocol used to transfer files from one system to another                                                                                                                                                                                                                           |
| Simple Mail Transfer Protocol                     | `SMTP`      | A protocol used to send and receive emails                                                                                                                                                                                                                                                     |
| Hypertext Transfer Protocol                       | `HTTP`      | A client-server protocol used to send and receive data over the internet                                                                                                                                                                                                                       |
| Server Message Block                              | `SMB`       | A protocol used to share files, printers, and other resources in a network                                                                                                                                                                                                                     |
| Network File System                               | `NFS`       | A protocol used to access files over a network                                                                                                                                                                                                                                                 |
| Simple Network Management Protocol                | `SNMP`      | A protocol used to manage network devices                                                                                                                                                                                                                                                      |
| Wi-Fi Protected Access                            | `WPA`       | WPA is a wireless security protocol that uses a password to protect wireless networks from unauthorized access.                                                                                                                                                                                |
| Temporal Key Integrity Protocol                   | `TKIP`      | TKIP is also a security protocol used in wireless networks but less secure.                                                                                                                                                                                                                    |
| Network Time Protocol                             | `NTP`       | It is used to synchronize the timing of computers on a network.                                                                                                                                                                                                                                |
| Virtual Local Area Network                        | `VLAN`      | It is a way to segment a network into multiple logical networks.                                                                                                                                                                                                                               |
| VLAN Trunking Protocol                            | `VTP`       | VTP is a Layer 2 protocol that is used to establish and maintain a virtual LAN (VLAN) spanning multiple switches.                                                                                                                                                                              |
| Routing Information Protocol                      | `RIP`       | RIP is a distance-vector routing protocol used in local area networks (LANs) and wide area networks (WANs).                                                                                                                                                                                    |
| Open Shortest Path First                          | `OSPF`      | It is an interior gateway protocol (IGP) for routing traffic within a single Autonomous System (AS) in an Internet Protocol (IP) network.                                                                                                                                                      |
| Interior Gateway Routing Protocol                 | `IGRP`      | IGRP is a Cisco proprietary interior gateway protocol designed for routing within autonomous systems.                                                                                                                                                                                          |
| Enhanced Interior Gateway Routing Protocol        | `EIGRP`     | It is an advanced distance-vector routing protocol that is used to route IP traffic within a network.                                                                                                                                                                                          |
| Pretty Good Privacy                               | `PGP`       | PGP is an encryption program that is used to secure emails, files, and other types of data.                                                                                                                                                                                                    |
| Network News Transfer Protocol                    | `NNTP`      | NNTP is a protocol used for distributing and retrieving messages in newsgroups across the internet.                                                                                                                                                                                            |
| Cisco Discovery Protocol                          | `CDP`       | It is a proprietary protocol developed by Cisco Systems that allows network administrators to discover and manage Cisco devices connected to the network.                                                                                                                                      |
| Hot Standby Router Protocol                       | `HSRP`      | HSRP is a protocol used in Cisco routers to provide redundancy in the event of a router or other network device failure.                                                                                                                                                                       |
| Virtual Router Redundancy Protocol                | `VRRP`      | It is a protocol used to provide automatic assignment of available Internet Protocol (IP) routers to participating hosts.                                                                                                                                                                      |
| Spanning Tree Protocol                            | `STP`       | STP is a network protocol used to ensure a loop-free topology in Layer 2 Ethernet networks.                                                                                                                                                                                                    |
| Terminal Access Controller Access-Control System  | `TACACS`    | TACACS is a protocol that provides centralized authentication, authorization, and accounting for network access.                                                                                                                                                                               |
| Session Initiation Protocol                       | `SIP`       | It is a signaling protocol used for establishing and terminating real-time voice, video and multimedia sessions over an IP network.                                                                                                                                                            |
| Voice Over IP                                     | `VOIP`      | VOIP is a technology that allows for telephone calls to be made over the internet.                                                                                                                                                                                                             |
| Extensible Authentication Protocol                | `EAP`       | EAP is a framework for authentication that supports multiple authentication methods, such as passwords, digital certificates, one-time passwords, and public-key authentication.                                                                                                               |
| Lightweight Extensible Authentication Protocol    | `LEAP`      | LEAP is a proprietary wireless authentication protocol developed by Cisco Systems. It is based on the Extensible Authentication Protocol (EAP) used in the Point-to-Point Protocol (PPP).                                                                                                      |
| Protected Extensible Authentication Protocol      | `PEAP`      | PEAP is a security protocol that provides an encrypted tunnel for wireless networks and other types of networks.                                                                                                                                                                               |
| Systems Management Server                         | `SMS`       | SMS is a systems management solution that helps organizations manage their networks, systems, and mobile devices.                                                                                                                                                                              |
| Microsoft Baseline Security Analyzer              | `MBSA`      | It is a free security tool from Microsoft that is used to detect potential security vulnerabilities in Windows computers, networks, and systems.                                                                                                                                               |
| Supervisory Control and Data Acquisition          | `SCADA`     | It is a type of industrial control system that is used to monitor and control industrial processes, such as those in manufacturing, power generation, and water and waste treatment.                                                                                                           |
| Virtual Private Network                           | `VPN`       | VPN is a technology that allows users to create a secure, encrypted connection to another network over the internet.                                                                                                                                                                           |
| Internet Protocol Security                        | `IPsec`     | IPsec is a protocol used to provide secure, encrypted communication over a network. It is commonly used in VPNs, or Virtual Private Networks, to create a secure tunnel between two devices.                                                                                                   |
| Point-to-Point Tunneling Protocol                 | `PPTP`      | It is a protocol used to create a secure, encrypted tunnel for remote access.                                                                                                                                                                                                                  |
| Network Address Translation                       | `NAT`       | NAT is a technology that allows multiple devices on a private network to connect to the internet using a single public IP address. NAT works by translating the private IP addresses of devices on the network into a single public IP address, which is then used to connect to the internet. |
| Carriage Return Line Feed                         | `CRLF`      | Combines two control characters to indicate the end of a line and a start of a new one for certain text file formats.                                                                                                                                                                          |
| Asynchronous JavaScript and XML                   | `AJAX`      | Web development technique that allows creating dynamic web pages using JavaScript and XML/JSON.                                                                                                                                                                                                |
| Internet Server Application Programming Interface | `ISAPI`     | Allows to create performance-oriented web extensions for web servers using a set of APIs.                                                                                                                                                                                                      |
| Uniform Resource Identifier                       | `URI`       | It is a syntax used to identify a resource on the Internet.                                                                                                                                                                                                                                    |
| Uniform Resource Locator                          | `URL`       | Subset of URI that identifies a web page or another resource on the Internet, including the protocol and the domain name.                                                                                                                                                                      |
| Internet Key Exchange                             | `IKE`       | IKE is a protocol used to set up a secure connection between two computers. It is used in virtual private networks (VPNs) to provide authentication and encryption for data transmission, protecting the data from outside eavesdropping and tampering.                                        |
| Generic Routing Encapsulation                     | `GRE`       | This protocol is used to encapsulate the data being transmitted within the VPN tunnel.                                                                                                                                                                                                         |
| Remote Shell                                      | `RSH`       | It is a program under Unix that allows executing commands and programs on a remote computer.                                                                                                                                                                                                   |


## Common protocols

**Transmission Control Protocol (TCP)**

- **Description**: TCP is a connection-oriented protocol used for reliable data transmission. It establishes a virtual connection between two devices before data transmission using a Three-Way Handshake. This connection persists until data transfer is complete, ensuring reliable communication.
- **Key Features**: Reliable but slower due to overhead in connection establishment and maintenance.

| **Protocol**                                              | **Acronym**  | **Port**         | **Description**                                                                                                                                                                    |
| --------------------------------------------------------- | ------------ | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Telnet                                                    | `Telnet`     | `23`             | Remote login service                                                                                                                                                               |
| Secure Shell                                              | `SSH`        | `22`             | Secure remote login service                                                                                                                                                        |
| Simple Network Management Protocol                        | `SNMP`       | `161-162`        | Manage network devices                                                                                                                                                             |
| Hyper Text Transfer Protocol                              | `HTTP`       | `80`             | Used to transfer webpages                                                                                                                                                          |
| Hyper Text Transfer Protocol Secure                       | `HTTPS`      | `443`            | Used to transfer secure webpages                                                                                                                                                   |
| Domain Name System                                        | `DNS`        | `53`             | Lookup domain names                                                                                                                                                                |
| File Transfer Protocol                                    | `FTP`        | `20-21`          | Used to transfer files                                                                                                                                                             |
| Trivial File Transfer Protocol                            | `TFTP`       | `69`             | Used to transfer files                                                                                                                                                             |
| Network Time Protocol                                     | `NTP`        | `123`            | Synchronize computer clocks                                                                                                                                                        |
| Simple Mail Transfer Protocol                             | `SMTP`       | `25`             | Used for email transfer                                                                                                                                                            |
| Post Office Protocol                                      | `POP3`       | `110`            | Used to retrieve emails                                                                                                                                                            |
| Internet Message Access Protocol                          | `IMAP`       | `143`            | Used to access emails                                                                                                                                                              |
| Server Message Block                                      | `SMB`        | `445`            | Used to transfer files                                                                                                                                                             |
| Network File System                                       | `NFS`        | `111`, `2049`    | Used to mount remote systems                                                                                                                                                       |
| Bootstrap Protocol                                        | `BOOTP`      | `67`, `68`       | Used to bootstrap computers                                                                                                                                                        |
| Kerberos                                                  | `Kerberos`   | `88`             | Used for authentication and authorization                                                                                                                                          |
| Lightweight Directory Access Protocol                     | `LDAP`       | `389`            | Used for directory services                                                                                                                                                        |
| Remote Authentication Dial-In User Service                | `RADIUS`     | `1812`, `1813`   | Used for authentication and authorization                                                                                                                                          |
| Dynamic Host Configuration Protocol                       | `DHCP`       | `67`, `68`       | Used to configure IP addresses                                                                                                                                                     |
| Remote Desktop Protocol                                   | `RDP`        | `3389`           | Used for remote desktop access                                                                                                                                                     |
| Network News Transfer Protocol                            | `NNTP`       | `119`            | Used to access newsgroups                                                                                                                                                          |
| Remote Procedure Call                                     | `RPC`        | `135`, `137-139` | Used to call remote procedures                                                                                                                                                     |
| Identification Protocol                                   | `Ident`      | `113`            | Used to identify user processes                                                                                                                                                    |
| Internet Control Message Protocol                         | `ICMP`       | `0-255`          | Used to troubleshoot network issues                                                                                                                                                |
| Internet Group Management Protocol                        | `IGMP`       | `0-255`          | Used for multicasting                                                                                                                                                              |
| Oracle DB (Default/Alternative) Listener                  | `oracle-tns` | `1521`/`1526`    | The Oracle database default/alternative listener is a service that runs on the database host and receives requests from Oracle clients.                                            |
| Ingres Lock                                               | `ingreslock` | `1524`           | Ingres database is commonly used for large commercial applications and as a backdoor that can execute commands remotely via RPC.                                                   |
| Squid Web Proxy                                           | `http-proxy` | `3128`           | Squid web proxy is a caching and forwarding HTTP web proxy used to speed up a web server by caching repeated requests.                                                             |
| Secure Copy Protocol                                      | `SCP`        | `22`             | Securely copy files between systems                                                                                                                                                |
| Session Initiation Protocol                               | `SIP`        | `5060`           | Used for VoIP sessions                                                                                                                                                             |
| Simple Object Access Protocol                             | `SOAP`       | `80`, `443`      | Used for web services                                                                                                                                                              |
| Secure Socket Layer                                       | `SSL`        | `443`            | Securely transfer files                                                                                                                                                            |
| TCP Wrappers                                              | `TCPW`       | `113`            | Used for access control                                                                                                                                                            |
| Internet Security Association and Key Management Protocol | `ISAKMP`     | `500`            | Used for VPN connections                                                                                                                                                           |
| Microsoft SQL Server                                      | `ms-sql-s`   | `1433`           | Used for client connections to the Microsoft SQL Server.                                                                                                                           |
| Kerberized Internet Negotiation of Keys                   | `KINK`       | `892`            | Used for authentication and authorization                                                                                                                                          |
| Open Shortest Path First                                  | `OSPF`       | `89`             | Used for routing                                                                                                                                                                   |
| Point-to-Point Tunneling Protocol                         | `PPTP`       | `1723`           | Is used to create VPNs                                                                                                                                                             |
| Remote Execution                                          | `REXEC`      | `512`            | This protocol is used to execute commands on remote computers and send the output of commands back to the local computer.                                                          |
| Remote Login                                              | `RLOGIN`     | `513`            | This protocol starts an interactive shell session on a remote computer.                                                                                                            |
| X Window System                                           | `X11`        | `6000`           | It is a computer software system and network protocol that provides a graphical user interface (GUI) for networked computers.                                                      |
| Relational Database Management System                     | `DB2`        | `50000`          | RDBMS is designed to store, retrieve and manage data in a structured format for enterprise applications such as financial systems, customer relationship management (CRM) systems. |


**User Datagram Protocol (UDP)**

- **Description**: UDP is a connectionless protocol used for faster data transmission. It does not establish a connection before data transmission, making it faster but less reliable compared to TCP.
- **Key Features**: Faster transmission but lacks reliability as it doesn't ensure data delivery.


| **Protocol**                        | **Acronym**  | **Port**    | **Description**                                                                                                                                    |
| ----------------------------------- | ------------ | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Domain Name System                  | `DNS`        | `53`        | It is a protocol to resolve domain names to IP addresses.                                                                                          |
| Trivial File Transfer Protocol      | `TFTP`       | `69`        | It is used to transfer files between systems.                                                                                                      |
| Network Time Protocol               | `NTP`        | `123`       | It synchronizes computer clocks in a network.                                                                                                      |
| Simple Network Management Protocol  | `SNMP`       | `161`       | It monitors and manages network devices remotely.                                                                                                  |
| Routing Information Protocol        | `RIP`        | `520`       | It is used to exchange routing information between routers.                                                                                        |
| Internet Key Exchange               | `IKE`        | `500`       | Internet Key Exchange                                                                                                                              |
| Bootstrap Protocol                  | `BOOTP`      | `68`        | It is used to bootstrap hosts in a network.                                                                                                        |
| Dynamic Host Configuration Protocol | `DHCP`       | `67`        | It is used to assign IP addresses to devices in a network dynamically.                                                                             |
| Telnet                              | `TELNET`     | `23`        | It is a text-based remote access communication protocol.                                                                                           |
| MySQL                               | `MySQL`      | `3306`      | It is an open-source database management system.                                                                                                   |
| Terminal Server                     | `TS`         | `3389`      | It is a remote access protocol used for Microsoft Windows Terminal Services by default.                                                            |
| NetBIOS Name                        | `netbios-ns` | `137`       | It is used in Windows operating systems to resolve NetBIOS names to IP addresses on a LAN.                                                         |
| Microsoft SQL Server                | `ms-sql-m`   | `1434`      | Used for the Microsoft SQL Server Browser service.                                                                                                 |
| Universal Plug and Play             | `UPnP`       | `1900`      | It is a protocol for devices to discover each other on the network and communicate.                                                                |
| PostgreSQL                          | `PGSQL`      | `5432`      | It is an object-relational database management system.                                                                                             |
| Virtual Network Computing           | `VNC`        | `5900`      | It is a graphical desktop sharing system.                                                                                                          |
| X Window System                     | `X11`        | `6000-6063` | It is a computer software system and network protocol that provides GUI on Unix-like systems.                                                      |
| Syslog                              | `SYSLOG`     | `514`       | It is a standard protocol to collect and store log messages on a computer system.                                                                  |
| Internet Relay Chat                 | `IRC`        | `194`       | It is a real-time Internet text messaging (chat) or synchronous communication protocol.                                                            |
| OpenPGP                             | `OpenPGP`    | `11371`     | It is a protocol for encrypting and signing data and communications.                                                                               |
| Internet Protocol Security          | `IPsec`      | `500`       | IPsec is also a protocol that provides secure, encrypted communication. It is commonly used in VPNs to create a secure tunnel between two devices. |
| Internet Key Exchange               | `IKE`        | `11371`     | It is a protocol for encrypting and signing data and communications.                                                                               |
| X Display Manager Control Protocol  | `XDMCP`      | `177`       | XDMCP is a network protocol that allows a user to remotely log in to a computer running the X11.                                                   |


**Internet Control Message Protocol (ICMP)**

- **Description**: ICMP is used for error reporting and status information between devices on the Internet. It includes request and message types for various network troubleshooting and management tasks.

- **Request Types**: 

| **Request Type**       | **Description**                                                                                                                                                                                                                                       |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Echo Request`         | This message tests whether a device is reachable on the network. When a device sends an echo request, it expects to receive an echo reply message. For example, the tools `tracert` (Windows) or `traceroute` (Linux) always send ICMP echo requests. |
| `Timestamp Request`    | This message determines the time on a remote device.                                                                                                                                                                                                  |
| `Address Mask Request` | This message is used to request the subnet mask of a device.                                                                                                                                                                                          |

- **Message Types**: 

| **Message Type**          | **Description**                                                                                                                  |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `Echo reply`              | This message is sent in response to an echo request message.                                                                     |
| `Destination unreachable` | This message is sent when a device cannot deliver a packet to its destination.                                                   |
| `Redirect`                | A router sends this message to inform a device that it should send its packets to a different router.                            |
| `time exceeded`           | This message is sent when a packet has taken too long to reach its destination.                                                  |
| `Parameter problem`       | This message is sent when there is a problem with a packet's header.                                                             |
| `Source quench`           | This message is sent when a device receives packets too quickly and cannot keep up. It is used to slow down the flow of packets. |

- **TTL**: Time-to-Live field in ICMP packet header limits packet lifetime, preventing indefinite circulation. It also helps determine packet hops and approximate distance to destination. Each time a packet passes through a router, the router decrements the `TTL value by 1`. When the TTL value reaches `0`, the router discards the packet and sends an ICMP `Time Exceeded` message back to the sender.



**Voice over Internet Protocol (VoIP)**

- **Description**: VoIP enables voice and multimedia communication over the internet, replacing traditional phone lines. It uses protocols like SIP and H.323 for session initiation, maintenance, and termination.
- **Protocols**: SIP (Session Initiation Protocol), H.323.
- **Common Ports**: TCP/5060, TCP/5061 (SIP).
- **Information Disclosure**: SIP OPTIONS request can enumerate users for potential attacks. Discovery of SEPxxxx.cnf file for Cisco Unified IP Phone configurations.
  
Most common SIP requests and methods :

| **Method** | **Description**                                                                                                    |
| ---------- | ------------------------------------------------------------------------------------------------------------------ |
| `INVITE`   | Initiates a session or invites another endpoint to participate.                                                    |
| `ACK`      | Confirms the receipt of an INVITE request.                                                                         |
| `BYE`      | Terminate a session.                                                                                               |
| `CANCEL`   | Cancels a pending INVITE request.                                                                                  |
| `REGISTER` | Registers a SIP user agent (UA) with a SIP server.                                                                 |
| `OPTIONS`  | Requests information about the capabilities of a SIP server or user agent, such as the types of media it supports. |


## Wireless Networks Fundamentals

- **Definition:** Wireless networks facilitate data transmission between devices without physical connections.
- **Technology:** Utilizes radio frequency (RF) signals for communication.

#### WiFi Connection Protocol (IEEE 802.11)

- **Association Process:**
  1. **Association Request:** Device initiates connection request to Wireless Access Point (WAP).

The connection request frame contains various fields of information, including the following but not limited to:

|                                |                                                                                              |
| ------------------------------ | -------------------------------------------------------------------------------------------- |
| `MAC address`                  | A unique identifier for the device's wireless adapter.                                       |
| `SSID`                         | The network name, also known as the `Service Set Identifier` of the WiFi network.            |
| `Supported data rates`         | A list of the data rates the device can communicate.                                         |
| `Supported channels`           | A list of the `channels` (frequencies) on which the device can communicate.                  |
| `Supported security protocols` | A list of the security protocols that the device is capable of using, such as `WPA2`/`WPA3`. |

  1. **Association Response:** WAP responds with parameters including challenge string.
  2. **Challenge-Response:** Device computes response to challenge using predetermined algorithm.
  3. **Authentication:** WAP verifies response, grants or denies access based on authentication outcome.



Some packets can get lost, so the so-called `CRC` checksum has been integrated. **Cyclic Redundancy Check** (`CRC`) is an error-detection mechanism used in the WEP protocol to protect against data corruption in wireless communications

When the destination device receives the packet, the CRC value is recalculated and compared to the original value. If the values match, the data has been transmitted successfully without any errors. However, if the values do not match, the data has been corrupted and needs to be retransmitted.

Because the `CRC` value is calculated using the `plaintext` data in the packet rather than the encrypted data. We can use the `CRC` to determine the plaintext data in the packet, even if the data is encrypted.


#### Security Features Overview

- **Encryption:** Critical for safeguarding data confidentiality during transmission.
	- WEP
	- WPA2
	- WP3
- **Access Control:** Regulates network access, often implemented via passwords or MAC address filtering.
- **Firewall:** Acts as a barrier against unauthorized access and malicious traffic.

#### Encryption Protocols

- **WEP (Wired Equivalent Privacy):**
  - **Algorithm:** Utilizes RC4 cipher.
  - **Key Length:** Available in WEP-40/WEP-64 (40-bit) and WEP-104 (104-bit).
  - **Vulnerabilities:** Susceptible to various attacks due to weak key management and encryption methodology.
  - **Shared key** for authentication, which means the same key is used for encryption and authentication


- **Initialization Vector (IV):** WEP uses a 24-bit IV to encrypt data packets. However, this IV is too short, which means it repeats over time. Attackers can exploit this by capturing enough packets and analyzing them to deduce the secret key.
    
- **Static Secret Key:** WEP uses a static secret key shared among all users on the network. Once this key is compromised, all data transmitted over the network becomes accessible to attackers. Additionally, there's no mechanism for key management or rotation.

Attackers can exploit the Initialization Vector (IV) in WEP encryption by capturing enough encrypted packets from the network. Because WEP uses a relatively short 24-bit IV, it repeats after a certain number of packets. When attackers capture multiple packets encrypted with the same IV, they can use statistical analysis to deduce patterns in the encryption and potentially recover the secret key. This weakness allows attackers to decrypt intercepted traffic and gain unauthorized access to the network.



- **WPA (WiFi Protected Access):**
  - **Strengths:** Provides enhanced security compared to WEP, leveraging AES encryption.
  - **Versions:** Includes WPA2 and the more recent WPA3 for improved security measures.

#### EAP (Extensible Authentication Protocol):

1. **Definition**: 
   - EAP is an authentication framework frequently used in wireless networks and point-to-point connections.
   - It provides a method for a client (like a user's device) to authenticate to a server (like an access point) before gaining access to the network.

2. **Key Features**:
   - Extensible: Supports various authentication methods.
   - Flexible: Can accommodate diverse network infrastructures.
   - Secure: Protects authentication credentials during transmission.

3. **Authentication Methods**:
   - EAP-TLS (Transport Layer Security): Uses digital certificates for authentication.
   - EAP-TTLS (Tunneled TLS): Creates an encrypted tunnel for authentication.
   - EAP-PEAP (Protected EAP): Similar to EAP-TTLS, often used with Microsoft products.
   - EAP-SIM (Subscriber Identity Module): Common in GSM and UMTS networks for SIM card authentication.
   - EAP-AKA (Authentication and Key Agreement): Derived from EAP-SIM, used in 3GPP networks.

4. **Protocol Operation**:
   - EAP operates between the link layer (such as PPP or IEEE 802.1X) and the authentication protocol layer.
   - It begins with a negotiation phase where the server proposes supported methods and the client selects one.
   - Authentication occurs within an encrypted tunnel, ensuring privacy and security.
#### LEAP (Lightweight Extensible Authentication Protocol):

1. **Definition**: 
   - LEAP is a proprietary EAP authentication method developed by Cisco Systems.
   - Initially popular but now considered insecure due to vulnerabilities like dictionary attacks.

2. **Key Features**:
   - Fast: Offers quick authentication.
   - Integration: Often used in Cisco's wireless infrastructure.

3. **Protocol Operation**:
   - LEAP involves a challenge-response mechanism where the client encrypts the challenge with a hashed password.
   - Vulnerabilities arise due to weak password hashing, making it susceptible to dictionary attacks.

4. **Security Concerns**:
   - Vulnerable to dictionary attacks due to weak password hashing.
   - No mutual authentication between client and server.
   - Considered obsolete and insecure, not recommended for use.

#### PEAP (Protected Extensible Authentication Protocol):

1. **Definition**: 
   - PEAP is an EAP authentication framework designed to strengthen EAP by encapsulating it within a secure tunnel.
   - Developed by Cisco, Microsoft, and RSA Security.

2. **Key Features**:
   - Security: Provides protection against eavesdropping and man-in-the-middle attacks.
   - Compatibility: Widely supported across various platforms and operating systems.
   - Flexibility: Allows different inner authentication methods like EAP-TLS or MS-CHAPv2.

3. **Protocol Operation**:
   - Initiates with an unauthenticated phase where the server presents its digital certificate.
   - Establishes a TLS-encrypted tunnel for subsequent authentication, ensuring confidentiality.
   - Within the tunnel, EAP methods like EAP-TLS or MS-CHAPv2 are used for actual authentication.

4. **Deployment Recommendations**:
   - PEAP with EAP-TLS offers strong security but requires client-side certificates.
   - PEAP with MS-CHAPv2 is simpler to deploy, using username/password authentication.


--- 

- WPA/2/3 sont des protocoles de sécurité utilisés pour sécuriser la communication sur les réseaux sans fil en fournissant un chiffrement des données et en empêchant les accès non autorisés au réseau.

- L/P/EAP quant à eux, sont des protocoles d'authentification utilisés pour vérifier l'identité des utilisateurs et des appareils qui tentent de se connecter au réseau sans fil. Ils permettent de s'assurer que seuls les utilisateurs autorisés peuvent accéder au réseau.

--- 
#### TACACS (Terminal Access Controller Access-Control System)

1. **Definition**:
    
    - TACACS is a security protocol used for controlling access to network devices, especially in military and government environments.
    - Developed by the Department of Defense (DoD) in the United States.
2. **Key Features**:
    
    - Access Control: Regulates who can access network terminals and devices.
    - Authentication: Requires users to authenticate before granting access.
    - Authorization: Defines user privileges and permissions based on roles.
    - Auditing: Records user activities for monitoring and compliance purposes.
3. **Components**:
    
    - Terminal Access Controller (TAC): Hardware or software device responsible for enforcing access control policies.
    - TACACS+ Server: Centralized server handling authentication, authorization, and accounting.
    - TACACS+ Client: Network device requesting access to resources, communicates with the TACACS+ server.
4. **Protocol Operation**:
    
    - TACACS+ operates over TCP port 49.
    - Authentication involves a three-step process: Authentication, Authorization, and Accounting (AAA).
    - Communication between the client and server is encrypted for security.
5. **Security Benefits**:
    
    - Granular Control: Allows fine-grained control over access permissions.
    - Accountability: Enables tracking of user actions for auditing and compliance.
    - Scalability: Supports large-scale networks with distributed access control policies.
6. **Deployment Considerations**:
    
    - Suitable for environments requiring stringent access control and audit capabilities.
    - Integrates well with existing network infrastructure, including routers, switches, and firewalls.
7. **Alternatives**:
    
    - RADIUS (Remote Authentication Dial-In User Service): Another widely used AAA protocol, more common in general networking environments.
    - Diameter: Evolved version of RADIUS, designed for modern telecommunications networks.

#### Disassociation Attack

- **Attack Vector:** Involves sending disassociation frames to disrupt communication between WAP and clients.
- **Objective:** Primarily used to create network disruptions or as a precursor to more sophisticated attacks.

#### Wireless Network Hardening Strategies

- **Disabling Broadcasting:**
  - **Purpose:** Conceals SSID to minimize visibility of the network, increasing difficulty for unauthorized users to identify and access it.

- **WPA (WiFi Protected Access):**
  - **Implementation:** Deployment of WPA2 or WPA3 for robust encryption and authentication capabilities, crucial for securing wireless communications.

- **MAC Filtering:**
  - **Functionality:** Permits or denies network access based on predefined MAC address lists, adding an additional layer of access control.

- **Deploying EAP-TLS:**
  - **Methodology:** Leverages digital certificates and Public Key Infrastructure (PKI) for strong authentication and encryption, enhancing overall network security posture.

## Virtual Private Networks (VPN) 

**1. What is a VPN?**

- A technology enabling secure and encrypted connections between a private network and remote devices.
- Provides secure access to network resources and services remotely.

**2. Why Use VPNs?**

- Encrypts connection, making it difficult for attackers to intercept data.
- Allows remote access to network resources from anywhere with an internet connection.
- Cost-effective solution for remote access compared to leased lines or dedicated connections.

**3. Components and Requirements:**

- **VPN Client:** Installed on remote devices to establish and maintain VPN connections (e.g., OpenVPN).
- **VPN Server:** Responsible for accepting VPN connections and routing traffic.
- **Encryption:** Utilizes encryption algorithms and protocols like AES and IPsec.
- **Authentication:** VPN server and client authenticate each other for a secure connection.

**4. VPN Connection Ports:**

- TCP/1723 for PPTP VPN connections.
- UDP/500 for IKEv1 and IKEv2 VPN connections.

**5. IPsec:**

- **Definition:** Internet Protocol Security providing encryption and authentication for internet communications.
- **Protocols Used:** AH (Authentication Header) and ESP (Encapsulating Security Payload).
- **Modes:** Transport Mode (end-to-end communication) and Tunnel Mode (VPN tunnel between networks).

**6. Necessary Protocols for IPsec VPN Traffic:**

- **IP:** UDP/50-51 for routing packets.
- **IKE:** UDP/500 for negotiating secure keys.
- **ESP:** UDP/4500 for encrypting VPN traffic.

**7. PPTP:**

- **Definition:** Point-to-Point Tunneling Protocol for creating VPNs.
- **Function:** Establishes a secure tunnel between client and server, encapsulating data.
- **Security Concerns:** Vulnerabilities make it obsolete and insecure.
- **Alternatives:** L2TP/IPsec, IPsec/IKEv2, OpenVPN for more secure options.

**Note:** Since 2012, PPTP is no longer considered secure due to vulnerabilities in the authentication method (MSCHAPv2) using outdated DES encryption.

## Cisco IOS: Vendor Specific Information

**Overview:**

- Cisco IOS is the operating system for Cisco network devices like routers and switches.
- It offers IPv6 support, QoS, security features (encryption, authentication), virtualization features (VPLS, VRF), etc.
- Managed through CLI and GUI.
- Supports various protocols and services: routing protocols, switching protocols, network services, security features.

**Passwords:**

- User Password: For logging in.
- Enable Password: For "enable" mode. The "enable" mode is the mode where you have access to advanced functions and settings.
- Secret: For securing access to certain functions.
- Enable Secret: Extra-secure password for "enable" mode.

**VLANs:**

- Logical grouping of network endpoints on switches.
- Segments networks based on factors like department or function.
- Offers benefits like better organization, increased security, simplified administration, and increased performance.

Cisco switches provide the `VLAN` IDs/numbers 1-4094 (`0` and `4095` are reserved IDs and cannot be used); IDs 1-1005 (`VLAN 1` is known as the `default VLAN` and cannot/should not be altered nor deleted) are known as `normal-range` `VLANs`, with IDs 1002-1005 being reserved for `Token Ring` and `Fiber Distributed Data Interface` (`FDDI`) `VLANs`, while IDs 1006-4094 are known as `extended-range` `VLANs`. By default, any customization applied for `normal-range` `VLANs` is saved in the `VLAN` database (the `vland.dat` file), in contrast to `extended-range` `VLANs`, which do not have their customizations saved. `VLANs` 2-1001 stored in `vlan.dat` can have parameters including name, type, state, and maximum transmission unit (`MTU`).



**VLAN Memberships:**

- Ports assigned to VLANs statically or dynamically.
- Static: Manual assignment per port.
- Dynamic: Based on MAC addresses or protocols.

The system administrator can register the `MAC` addresses in a centralized `VLAN` management service/database, such as the `VLAN Membership Policy Server` (`VMPS`)


**Access and Trunk Ports:**

- Access Ports: Belong to one VLAN, carry traffic for that VLAN.
- Trunk Ports: Carry traffic for multiple VLANs.

**VLAN Identification:**

- ISL: Cisco-proprietary, deprecated.
- IEEE 802.1Q: Industry standard, adds VLAN tag to Ethernet frame.

!["802.1Q"](/images/802.1Q.png)


`Tag protocol identifier` (`TPID`) is a 16-bit field always set to `0x8100` to identify the `Ethernet` frame as an `802.1Q`-tagged frame. `Tag Control Information` (`TCI`) is a 16-bit field containing `Priority code point` (`PCP`), `Drop eligible indicator` (`DEI`) (previously known as `Canonical format indicator` (`CFI`)), and `VLAN identifier` (`VID`). The main field concerning `VLANs` is `VID`, occupying the low-order 12-bits of `TCI`. Since it is 12 bits, it allows 2^12 - 2 = 4096 (remember, `0` and `4095` are reserved) `VLAN` IDs. Therefore, an `802.1Q`-tagged frame can contain information for 4094 `VLANs`; the practice of inserting multiple `802.1Q` tags within a single packet is known as `Double Tagging`, introduced by 802.1ad. `VLAN tagging` is the process of inserting `VLAN` information into an `802.1Q` `Ethernet header`, while `VLAN untagging` is the process of removing the `VLAN` information from an `802.1Q`-tagged `Ethernet` frame and forwarding the packet to the destined ports.


**VLAN-Capable NICs:**

- Some NICs support VLAN tagging.
- Can be configured in Linux and Windows.

**Analyzing VLAN Tagged Traffic:**

- Wireshark can analyze VLAN-tagged traffic.
- Filters like "vlan" and "vlan.id" can be used to isolate VLAN traffic.

Additionally, to enumerate the used `VLAN` IDs from a packet dump, we can utilize tshark:


```shell-session
tshark -r "The Ultimate PCAP v20221220.pcapng" -T fields -e vlan.id | sort -n -u

1
2
3
7
10
20
30
40
50
60
70
80
90
121
125
224
```


**VLAN Attacks:**

- VLAN Hopping: Exploits Dynamic Trunking Protocol (DTP) to jump between VLANs.
	- We can use tools such as Yersinia to perform `VLAN hopping` attacks:
	- An adversary needs to configure a host to mimic/act like a switch to take advantage of the automatic trunking port feature enabled by default on most switch ports. To exploit `VLAN hopping`, an adversary must be able to physically connect with a switch port that has `DTP` enabled. The adversary can abuse this connection by configuring a host connected to the switch on that specific port to spoof `802.1Q` signaling and the `DTP` packets. If successful, the switch will eventually establish a `trunk link` with the adversary's host, exposing the network packets, not only for a specific `VLAN`.
	
	
- Double-tagging VLAN Hopping 
		- An advanced attack that exploits the practice of VLAN double-tagging.
		- Attackers embed a hidden 802.1Q tag inside an Ethernet frame, allowing it to traverse to a different VLAN than intended.
	
	**Attack Steps:**
	
	1. **Send Double-Tagged Frame:**
	    
	    - Adversary sends a double-tagged 802.1Q Ethernet frame to the switch.
	    - Outer header contains VLAN ID of the adversary (native VLAN of the trunk port).
	    - Example: Native VLAN (e.g., VLAN 10), target VLAN (e.g., VLAN 30).
	2. **Arrival and Tag Stripping:**
	    
	    - Outer VLAN tag is seen destined for the native VLAN (e.g., VLAN 10).
	    - VLAN 10 tag is removed, and the frame is forwarded on all VLAN 10 ports.
	    - On the trunk port, VLAN 10 tag is stripped, but VLAN 30 tag remains intact.
	    - First switch does not inspect the VLAN 30 tag.
	3. **Forwarding Decision:**
	    
	    - Switch looks at the inner 802.1Q tag sent by the adversary.
	    - Decides to forward the frame for VLAN 30, the adversary's chosen VLAN.
	    - Second switch forwards the frame to the victim port directly or floods it based on MAC address table entry.
	
	**Tools for Execution:**
	
	- **Scapy:** Allows carrying out the double-tagging VLAN hopping attack programmatically.
	- **Yersinia:** Another tool capable of executing the double-tagging VLAN hopping attack.
	
	**Mitigation Techniques:**
	
	- **VLAN Access Control Lists (VACLs):** Implement VACLs to restrict VLAN traffic at Layer 2.
	- **Port Security:** Enable port security features to limit the number of MAC addresses per port.
	- **VLAN Pruning:** Configure VLAN pruning to prevent unnecessary VLAN traffic on trunk ports.
	- **Intrusion Detection Systems (IDS):** Employ IDS to detect and respond to abnormal VLAN hopping activity.
	

**VXLAN (Virtual eXtensible Local Area Network):**

- **Purpose:** Scalable Layer 2 overlay network over Layer 3 infrastructure.
- **Challenge Addressed:** Limitations of traditional Layer 2 networks in data center environments.
- **Key Features:**
    - Extends Layer 2 networks seamlessly across data center landscapes.
    - Uses VXLAN segments to isolate and secure network traffic.
    - Employs 24-bit VXLAN Network Identifier (VNI) for segment identification.
    - Supports up to 16 million VXLAN segments for scalability.
- **Use Cases:** Multi-tenant environments with virtual machines (VMs), large-scale data centers.


**Cisco Discovery Protocol (CDP):**

- **Purpose:** Layer 2 network protocol for gathering device information in Cisco networks.
- **Functionality:** Discovers and tracks network topology, aids in network management and troubleshooting.
- **Key Features:**
    - Provides information about directly connected Cisco devices (routers, switches, etc.).
    - Shares device name, IP address, port name, OS, hardware platform, and capabilities.
    - Enabled by default on Cisco devices but can be disabled for security reasons.


**Spanning Tree Protocol (STP):**

- **Purpose:** Prevents network loops in Ethernet networks with redundant connections.
- **Functionality:** Ensures loop-free topology and prevents packet circulation in loops.
- **Key Features:**
    - Uses 802.1w (Rapid STP) or 802.1d (Classic STP) versions.
    - Determines root switch, port roles (e.g., root port, designated port), and bridge IDs.
    - Configurable parameters include max age, hello time, forward delay.
    - Prevents link blocking and ensures network resiliency through multipathing.



## Key Exchange 

**Symmetric Encryption:**

- **AES (Advanced Encryption Standard)**: Symmetric encryption algorithm using keys of 128, 192, or 256 bits. Primarily used for large-scale data encryption.
- **DES (Data Encryption Standard)**: Former symmetric encryption algorithm using a 56-bit key. Used in the past but now largely obsolete due to its vulnerability.
- **3DES (Triple Data Encryption Standard)**: Enhanced version of DES that applies DES three times with three different keys for improved security. Used as a secure alternative to DES.


**Asymmetric Encryption:**

- **RSA (Rivest-Shamir-Adleman)**: Asymmetric encryption algorithm used for key encryption, digital signatures, and other security applications.
- **ECC (Elliptic Curve Cryptography)**: Family of asymmetric encryption algorithms based on elliptic curves, offering security comparable to RSA with shorter keys.


**Key Exchange:**

- **DH (Diffie-Hellman)**: Public key encryption protocol for secure key exchange.
- **ECDH (Elliptic Curve Diffie-Hellman)**: DH variant using elliptic curves for improved performance and security.
- **IKE (Internet Key Exchange)**: Protocol used to negotiate and establish Security Associations (SAs) in IPsec VPNs. There are several IKE modes:
	    - **Main Mode**: A mode where all security parameters are exchanged securely and authenticated in multiple steps.
	    - **Aggressive Mode**: A mode where security parameters are exchanged in a single step, making it faster but less secure than Main Mode.
	
	- **IKEv1**: Uses ISAKMP (Internet Security Association and Key Management Protocol) for negotiating security parameters.
    
    - **IKEv2**: Enhanced version of IKEv1, offering improved performance and security, as well as support for client mobility.


**Digital Signature:**

- **DSA (Digital Signature Algorithm)**: Digital signature algorithm used for message authentication and non-repudiation.
- **ECDSA (Elliptic Curve Digital Signature Algorithm)**: DSA variant based on elliptic curves.


**Authentication:**

- **HMAC (Hash-based Message Authentication Code)**: Authentication method based on hash functions, used with symmetric encryption algorithms.
- **PSK (Pre-Shared Key)**: Authentication mode used in network security protocols, where a key is shared in advance between parties.

## Authentication Protocols

1. **Kerberos**
	- Description: Key Distribution Center (KDC) based authentication protocol using tickets in domain environments.
  
2. **SRP** (Secure Remote Password)
	- Description: Password-based authentication protocol using cryptography to protect against eavesdropping and man-in-the-middle attacks.
  
3. **SSL**
	- Description: Cryptographic protocol for secure communication over a computer network.
  
4. **TLS**
	- Description: Successor to SSL, provides communication security over the internet using cryptography.
  
5. **OAuth**
	- Description: Open standard for authorization allowing third-party access to web resources without sharing passwords.
  
6. **OpenID**
	- Description: Decentralized authentication protocol enabling single identity sign-in across multiple websites.
  
7. **SAML**
	- Description: XML-based standard for securely exchanging authentication and authorization data between parties.
  
8. **2FA (Two-Factor Authentication)**
	- Description: Authentication method using two different factors to verify a user's identity.
  
9. **FIDO (Fast IDentity Online Alliance)**
	- Description: Consortium developing open standards for strong authentication.
  
10. **PKI (Public Key Infrastructure)**
    - Description: System for securely exchanging information using public and private keys for encryption and digital signatures.
  
11. **SSO (Single Sign-On)**
    - Description: Authentication method allowing a single set of credentials for access to multiple applications.
  
12. **MFA (Multi-Factor Authentication)**
    - Description: Authentication method using multiple factors (e.g., password, phone, biometric data) to verify identity.
  
13. **PAP (Password Authentication Protocol)**
    - Description: Simple authentication protocol sending user passwords in clear text over the network.
  
14. **CHAP (Challenge-Handshake Authentication Protocol)**
    - Description: Authentication protocol using a three-way handshake to verify user identity.
  
## TCP/UDP Connections

**IP Packet**

- **Definition**: Data area used by the network layer to transmit data.
- **Structure**:
  - Header: Contains routing and transmission information.
  - Payload: Actual data being transmitted.

**IP Header Fields**

- **Version**: Indicates the IP protocol version.
- **Internet Header Length**: Size of the header in 32-bit words.
- **Class of Service**: Indicates data transmission importance.
- **Total Length**: Total packet length in bytes.
- **Identification (ID)**: Identifies fragments of a packet.
- **Flags**: Indicate fragmentation.
- **Fragment Offset**: Indicates position of current fragment.
- **Time to Live**: Specifies packet lifespan on network.
- **Protocol**: Specifies transmission protocol (TCP/UDP).
- **Checksum**: Detects errors in the header.
- **Source/Destination**: Addresses of sender and recipient.
- **Options**: Optional routing information.
- **Padding**: Fills packet to full word length.

**IP Record-Route Field**

- **Purpose**: Records route to destination device.
- **Usage**: ICMP Echo Reply packets include passing device IP addresses.
- **Example**: Displayed when using `ping -R [destination]`.

**Traceroute**

- **Purpose**: Trace route to destination accurately.
- **Process**:
  1. Send TCP SYN packet with TTL of 1.
  2. Receive ICMP Time-Exceeded packet and note router IP.
  3. Repeat with increased TTL until response from destination.

**TCP**

- **Segments**: Divided into headers and payloads.
- **Header Fields**:
  - Source/Destination Port
  - Sequence/Confirmation Number
  - Control Flags
  - Window Size
  - Checksum
  - Urgent Pointer

**UDP**

- **Datagrams**: Small data packets.
- **Characteristics**:
  - Connectionless.
  - Data sent directly without prior connection.

**Blind Spoofing**

- **Definition**: Manipulating IP header to send false information.
- **Method**: 
  - Falsifying source/destination addresses.
  - Manipulating TCP packet fields.
- **Usage**: 
  - Disrupting network integrity.
  - Breaking connections.
  - Monitoring network traffic.
  - Intercepting information.

## Cryptography 

**1. Symmetric Encryption:**
- **Definition:** Uses same key for encryption and decryption.
- **Example Algorithms:** AES, DES.
- **Key Management:** Key distribution, storage, and exchange are critical.
- **Security:** Dependent on key secrecy.

**2. Asymmetric Encryption:**
- **Definition:** Uses two keys: public and private.
- **Example Algorithms:** RSA, PGP, ECC.
- **Key Advantage:** No need for secret key exchange.
- **Applications:** E-Signatures, SSL/TLS, VPNs.

**3. Data Encryption Standard (DES):**
- **Definition:** Symmetric-key block cipher.
- **Key Length:** Actual key length is 56 bits.
- **Triple DES (3DES):** Encrypts data with three rounds of encryption.
- **Security Limitations:** Vulnerable due to short key length.

**4. Advanced Encryption Standard (AES):**
- **Definition:** Symmetric encryption with longer key lengths.
- **Key Lengths:** AES-128, AES-192, AES-256.
- **Performance:** Faster and more efficient than DES.
- **Applications:** WLAN, IPsec, SSH.

**5. Cipher Modes:**
- **Electronic Code Book (ECB):** Not recommended due to vulnerability.
- **Cipher Block Chaining (CBC):** Default mode for AES, widely used.
- **Cipher Feedback (CFB):** Suitable for real-time encryption.
- **Output Feedback (OFB):** Better for data streams, used in PKCS and SSH.
- **Counter (CTR):** Encrypts real-time data streams.
- **Galois/Counter (GCM):** Protects confidentiality and integrity together.

**6. Considerations:**
- **Security vs. Efficiency:** Trade-offs in encryption methods.
- **Key Length:** Longer keys offer greater security.
- **Applications:** Choose encryption methods based on specific needs.
- **Mode Selection:** Depends on message characteristics and security requirements.
