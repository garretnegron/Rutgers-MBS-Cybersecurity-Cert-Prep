# Module 2: Network Operations
- Metwork Protocols
- Virtual Private Networks
- Firewalls, security zones, and proxy servers

## Network Protocols

A set of **rules** used by two or more devices on a network to describe the **order of delivery** and the **structure** of data.

### Transmission Control Protocol
**Tansmission Control Protocol (TCP)** is an internet communications protocol that allows two devices to form a connection and stream data.

> [!Note]
> TCP isn’t limited to just two devices. It established a direct connection between two endpoints, but the underlying network infrastructure can handle routing data packets across multiple devices.

TCP establishes a connection before any data is sent, confirming both devices are
reachable and ready to communicate. This is called the **three-way handshake**:

1. **SYN**: the client asks to open a connection
2. **SYN-ACK**: the server agrees and acknowledges
3. **ACK**: the client confirms, and the connection is open

After the handshake, a **request** is made. For example, visiting a webpage: the TCP
handshake happens first, then the browser sends an **HTTP request** (Layer 7) for the page.
The web server sends the page back as TCP segments, which our device reassembles in order
so we can view it.

On HTTPS sites, a **TLS handshake** happens after the TCP handshake to encrypt the connection and verify the server's identity before the request is sent.

### User Datagram Protocol
**User Datagram Protocol (UDP)** is a connectionless protocol that does not establish a connection between devices before transmission.

### Address Resolution Protocol (ARP)
**Address Resolution Protcol (ARP)** is a network protocol used to find the **MAC address**
of the next router or device on the path, using its **IP address**. It bridges Layer 3 (IP)
and Layer 2 (MAC) and only works within the local network.

1. The device broadcasts an **ARP request** to the whole local network:
   *"Who has 192.168.1.1? Tell me your MAC address."*
2. Only the device with that IP sends back an **ARP reply** containing its MAC address.
3. The answer is stored in the **ARP cache**, so the device doesn't have to ask again
   for a while.


### HyperText Transfer Protocol Secure (HTTPS)
**HTTPS** is a network protcol that provides a secure method of communciation between clients and website server.

**HyperText Tranfer Protocol (HTTP)** is considered insecure which is why many websites are being replaced by HTTPS. 

### Domain Name System (DNS)
**Domain Name System (DNS)** is a network prtotcol that translates internet domain names into IP addresses. When a client computer wishes to access a website domain using their internet browser, a query is sent to a dedicated DNS server. The DNS server then looks up the IP address that corresponds to the website domain.

DNS normally uses UDP on **port 53**. However, if the DNS reply to a request is large, it will switch to using the 
TCP protocol.

### Management Protocols
Used for monitoring and managing activity on a network. Include protocols for error reporting and optimizing performance on the network.
- **Simple Network Managment Protocol (SNMP)** is a network protocol used for monitoring and managing devices on a network. SNMP can reset a password on a network device or change its baseline configuration. It can also send requests to network devices for a report on how much of the network's bandwidth is being used up. In the TCP/IP model, SNMP occurs at the application layer.

- **Internet Control Message Protocol (ICMP)** is an internet protocol used by devices to tell each other about data transmission errors across the network. ICMP is used by a receiving device to send a report to the sending device about the data transmission. ICMP is commonly used as a quick way to troubleshoot network connectivity and latency by issuing "ping" command on a Linux OS. ICMP occurs at the **internet layer**.

### Security Protocols
- **Hypertext Transfer Protocol Secure (HTTPS)** is a network protocol that provides a secure method of communication between clients and website servers. HTTPS is a secure version of HTTP that uses secure sockets layer/transport layer security (SSL/TLS) encryption on all transmissions so that malicious actors cannot read the information contained. HTTPS uses port 443. In the TCP/IP model, HTTPS occurs at the application layer.

- **Secure File Transfer Protocol (SFTP)** is a secure protocol used to transfer files from one device to another over a network. SFTP uses **secure shell (SSH)**, typically through **TCP port 22**. SSH uses Advanced Encryption Standard (AES) and other types of encryption to ensure that unintended recipients cannot intercept the transmissions. In the TCP/IP model, SFTP occurs at the **application layer**. SFTP is used often with cloud storage. Every time a user uploads or downloads a file from cloud storage, the file is transferred using the SFTP protocol.

> [!NOTE]
> The encryption protocols mentioned **do not conceal** the source or destination IP address of network traffic. This means a malicious actor can still learn some basic information about the network traffic if they intercept it. 

## Additional Network Protocols 

### Network Address Translation (NAT)
Devices on a LAN use **private IP addresses** to talk to each other. To reach the public
internet, they share **one public IP address** that represents the whole network.

- **Outgoing:** the router replaces the device's private source IP with its public IP.
- **Incoming:** the router reverses it, sending the response back to the right private IP.
- Requires a **router or firewall** specifically configured to perform NAT.
- Works at the **Internet layer** (IP addresses) and **Transport layer** (port numbers)
  of the TCP/IP model.

> **Example:** Your laptop (`192.168.1.25`) requests a webpage. The router swaps in its
> public IP (`203.0.113.7`) before sending it out, then forwards the reply back to
> `192.168.1.25`.

### Dynamic Host Configuration Protocol (DHCP)
A **management protocol** at the **Application layer** that automatically configures
devices when they join a network. Working with the router, it gives each device:

- A **unique IP address**
- The address of the **DNS server**
- The address of the **default gateway** (the router)

| Role | Protocol | Port |
|---|---|---|
| DHCP server | UDP | 67 |
| DHCP client | UDP | 68 |

> **Example:** When your phone joins home Wi-Fi, DHCP assigns it an IP like
> `192.168.1.42`, tells it which DNS server to use, and sets the router as its gateway,
> with no manual setup needed.

### Address Resolution Protocol (ARP)
A **Network Access layer** protocol (TCP/IP model) that translates an **IP address** into
the **MAC address** of the device it belongs to. Devices on the same network talk to each
other using MAC addresses, so when a device knows the IP but not the MAC, it uses ARP.

- **IP address:** can change over time
- **MAC address:** tied to the device's network interface card (NIC)
- Works only **within the local network**: to reach outside, it finds the router's MAC

**How it works:**
1. The device broadcasts an **ARP request** to the local network:
   *"Who has 192.168.1.1? Tell me your MAC address."*
2. Only the device with that IP sends back an **ARP reply** with its MAC address.
3. Each device stores IP ↔ MAC matches in its **ARP cache** to avoid asking again.

**No port number:** ARP runs below the Transport layer, where port numbers live.

### Telnet
An **Application layer** protocol used to connect to and control a local or remote device
through a **command line**. It sends everything, including usernames and passwords, in
**clear text**, so anyone watching the network can read it.

| | Telnet | SSH |
|---|---|---|
| Purpose | Remote command-line access | Remote command-line access |
| Encryption | ❌ None (clear text) | ✅ Encrypted |
| Port | TCP 23 | TCP 22 |
| Use today | Legacy systems, testing | Standard for remote access |

> **Security takeaway:** Telnet has been replaced by SSH for remote access. Seeing
> port 23 open on a network is a common security red flag.

### Secure Shell (SSH)
An **Application layer** protocol that creates a **secure connection** to a remote system.
It provides **secure authentication** (password or SSH key) and **encrypted
communication**, replacing less secure protocols like **Telnet**.

- **Port:** TCP 22
- **Encrypted:** anyone watching the network can't read the traffic

> **Data example:** Data engineers use SSH to log into cloud servers (e.g., an EC2
> instance running Airflow), push code to GitHub with SSH keys, and open **SSH tunnels**
> to reach databases on private networks.


## Wireless Protocols
### IEEE 802.11 (WiFi)
A set of standards that define communciation for wioreless LANs

**Wifi Protected Access (WPA)** is a wireless security protocol for devices to connect to the internet.

### Wired Equivalent Privacy (WEP)
WEP is a wireless security protocol designed to provide users with the same level of privacy on wireless network connections as they have on wired network connections.
- Developed in 1999
- Largely **Out of Use** today


### Wi-Fi Protected Access (WPA)
WPA was developed in 2003 to improve upon WEP, address the security issues that it presented, and replace it.

The flaws with WEP were in the protocol itself and how the encryption was used. WPA addressed this weakness by using a protocol called **Temporal Key Integrity Protocol (TKIP)**. WPA encryption algorithm uses larger secret keys than WEPs, making it more difficult to guess the key by trial and error.

### WPA2 (2004)
The second version of **Wi-Fi Protected Access**, and still the most widely used
Wi-Fi security standard.

- Uses **AES** encryption, replacing WPA's weaker **TKIP**
- Uses **CCMP** for message authentication and integrity
- ⚠️ Vulnerable to **KRACK** (Key Reinstallation Attack), which led to WPA3

| | Personal | Enterprise |
|---|---|---|
| Best for | Home networks | Businesses |
| Setup | Quick and simple | More complex |
| Access | One shared passphrase on every device | Individual logins, centrally managed |
| Control | Change the password to remove someone | Admins grant or remove users anytime |
| Keys | Passphrase stored on each device | Users never see encryption keys |

### WPA3 (2018)
The newest Wi-Fi security standard, growing as more devices support it.

- **Fixes KRACK:** replaces WPA2's vulnerable handshake
- **SAE (Simultaneous Authentication of Equals):** a safer password handshake that stops
  attackers from capturing Wi-Fi traffic and cracking the password offline
- **Stronger encryption:** 128-bit (Personal), optional 192-bit (Enterprise)

## Firewalls and Network Security Measures
**Firewalls** are network security devices that monitor traffic to and from your network. It either allows traffic, or blocks it, based on defined set of security rules.

- **Port Filtering** is a firewall function that blocks or allows certain port numbers to limit unwanted communication.

- **Cloud-based Firewalls** are software firewalls that are hosted by a cloud service provider.

- **Stateful** is a class of firewall that keeps track of information passing through it and proactively filters out threats.

- **Stateless** is a class of firewall that operates based on predefined rules and does not keep track of infromartion from data packets.

### Next Generation Firewalls (NGFWs)
Benefits from in-depth security functions like:
- **Deep packet inspection**
- **Intrusion protection**
- **Threat intelligence**


## Virtual Private Network (VPN)
A network security service that **changes your public IP address and hides your virtual location** so that you can keep your data private when you are using a public network like the internet.

- **Encapsulation** is a process performed by a VPN service that protects your data by wrapping sensitive data in other data packets.

- **Security zone** is a segment of a network that protects the internal network from the internet.

- **Uncontrolled zone** is any network outside the organization's control.

- **Controlled zone** is a subnet that protects the internal network from the unctrolled zone.

**Network Segmentation** is a security technique that divides the network into segments. (***Security Zones** a part of this*)

### Areas in the Controlled Zone:
- DMZ - (*Ideally situated between two firewalls*)
- Internal Network<br>
*(Firewall between these two as well)*
- Restricted Zone

## Subnetting
The process of taking one large network and dividing it into several smaller, organized groups called **subnets**. 

- Subnetting divides up a network address range into smaller subnets within the network.
- The organized subnets are defined by the unique combination of the **IP address** and the **network mask** assigned to every device, effectively creating a "network within a network."

### Classless Inter-Domain Routing (CIDR)
A method of assigning **subnet masks** to IP addresses to create subnets. It replaced
**classful addressing** (Classes A–E, used in the 1980s), whose fixed-size blocks ran out
as the internet grew in the 1990s. CIDR lets networks be split into right-sized chunks,
which saves IPv4 addresses and **reduces routing table entries**.

**Format:** an IPv4 address + `/` + the **IP network prefix**

    198.51.100.0/24  →  covers 198.51.100.0 to 198.51.100.255

**How to read the prefix:** an IPv4 address has 32 bits. The prefix is how many bits
are **fixed** for the network; the remaining bits are free for devices.

$$
\text{Number of addresses} = 2^{\,32 - \text{prefix}}
$$

| CIDR | Fixed part | Addresses |
|---|---|---|
| `/8` | first number (`10.x.x.x`) | 16,777,216 |
| `/16` | first two numbers (`10.0.x.x`) | 65,536 |
| `/24` | first three numbers (`10.0.0.x`) | 256 |
| `/32` | all four (one exact address) | 1 |

**Bigger prefix = smaller network.**

> **Data example:** Cloud networks are defined in CIDR, e.g., an AWS VPC of `10.0.0.0/16`
> split into subnets like `10.0.1.0/24`. IP allowlists (Snowflake, Azure SQL) also use
> CIDR: `203.0.113.7/32` allows exactly one IP address.

Practice converting: [IPAddressGuide CIDR tool](https://www.ipaddressguide.com/cidr)

## Proxy Server
**A server that fulfills the requests of a client by forwarding them on to other servers.**

***Forward Proxy Server***<br>
Regulates and restricts a person's access to the internet.

***Reverse Proxy Server***<br>
Regulates and restricts the internet's access to an internal server.


##
## WireGuard VPN vs. IPSec VPN
Both are **VPN protocols** that encrypt traffic through a secure tunnel. Which to choose
depends on speed needs, compatibility with existing infrastructure, and business or
personal requirements.

| | WireGuard | IPSec |
|---|---|---|
| Age | Newer | Older, one of the earliest |
| Complexity | Simple, small codebase | More complex |
| Setup | Easy to configure and maintain | More involved |
| Speed | Faster | Generally slower |
| Compatibility | Growing | Built into most operating systems |
| Track record | Shorter | Long history, extensively tested |
| Open source | Yes | Open standard (many implementations) |
| Connections | Site-to-site and client-server | Site-to-site and client-server |

**Choose WireGuard for:** speed and simplicity (streaming, large downloads).
**Choose IPSec for:** compatibility and a proven, widely adopted standard.