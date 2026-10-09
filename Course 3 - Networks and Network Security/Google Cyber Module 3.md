# Module 3: Secure Against Network Intrusions

#### Common Network Intrusion Attacks:
- Malware
- Spoofing
- Packet sniffing
- Packet flooding

#### Attacks can harm an org by:
- Leaking valuable or confidential information
- Damaging an org's reputation
- Impacting customer retention
- Costing money and time

## How Intrusions Compromise your System
### Network Interception Attacks
Network interception attacks work by intercepting network traffic and stealing valuable information or interfering with the transmission in some way.

Malicious actors can use hardware or software tools to capture and inspect data in transit. This is referred to as `packet sniffing`.

### Backdoor Attacks
In cybersecurity, backdoors are **weaknesses intentionally left by programmers** or system and network administrators that bypass normal access control mechanisms.
Backdoors are intended to help programmers conduct troubleshooting or administrative tasks. However, backdoors **can also be installed by attackers** after they’ve compromised an organization to ensure they have **persistent access**.


### Denial of Service Attack (DoS)
A `DoS attack` is an attack that targets a network or server and floods it with network traffic.
> SEND so much traffic that server crashes, or is unable to respond to legitimate users.

#### Distributed Denial of Service Attack (DDoS)
A type of DoS attack that uses multiple devices or servers in different locations to flood the target network with unwanted traffic.

#### Types of Network Level DoS Attacks:

- **SYN (synchronize) Flood Attack**
  - Simulates a TCP connection and floods a server with SYN packets.
- **Internet Control Message Protocol (ICMP) Flood Attack**
  - Attacker repeatedly sending ICMP packets to a network server.
- **Ping of Death**
  - Hacker pings a system by sending it an oversized ICMP packet that is bigger than 64KB

### tcpdump

A **command-line network protocol analyzer** that captures ("sniffs") packets and prints
a readable summary of each one in the terminal, and optionally to a log file.

- **Lightweight:** low memory and CPU use
- **Open source:** built on the **libpcap** library
- **Text-based:** runs entirely in the terminal
- **Preinstalled** on many Linux distributions; can be installed on other Unix-based
  systems like macOS

**Reading the output:**

    14:02:31.123456 IP 192.168.1.25.52444 > 93.184.216.34.443: Flags [S], ...
    └── timestamp ─┘    └ source IP ┘└port┘  └─ dest IP ──┘└port┘

| Field | Meaning |
| --- | --- |
| **Timestamp** | When the packet was captured (hours:minutes:seconds.fraction) |
| **Source IP** | Where the packet came from |
| **Source port** | Port it was sent from (the number after the last `.`) |
| **Destination IP** | Where the packet is going |
| **Destination port** | Port it's going to (e.g., `443` = HTTPS) |

> **Note:** By default, tcpdump replaces IP addresses with **hostnames** and port numbers
> with **service names** (e.g., `443` → `https`). Use `-n` to turn off hostname lookup,
> and `-nn` to also show raw port numbers.

## Network Attack Tactics and Defense

***Passive Packet Sniffing*** is a type of attack where data packets are **read** in transit.

***Active Packet Sniffing*** is a type of attack where data packets are **manipulated** in transit.

***IP Spoofing*** is performed when an attacker changes the source IP of a data packet to impersonate an authorized system and gain access to a network.

- **On-path attack**
  - Malicious actor places themselves in the middle of an authorized connection and intercepts or alters the data in transit.
- **Replay attack**
  - An attacker intercepts valid network traffic and sends it again to trick a system into accepting it as legitimate.
- **Smurf attack**
  - An attacker sends spoofed ICMP requests to a network broadcast address, causing a flood of responses to the victim.

> Firewall rules can reject traffic that have same IP address as the local network.
