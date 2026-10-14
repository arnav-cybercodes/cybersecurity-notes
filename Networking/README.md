# Networking Fundamentals for Cybersecurity

## 1. What Is Computer Networking?

Computer networking is the process of connecting two or more devices so that they can exchange data and share resources using communication protocols.

Networking knowledge is essential for cybersecurity professionals because attacks, suspicious communications, command-and-control traffic, lateral movement, and data exfiltration often leave traces in network traffic.

### Types of Networks

| Network | Full Form | Description |
|---|---|---|
| PAN | Personal Area Network | Short-range personal devices |
| LAN | Local Area Network | Devices within a home, office, or lab |
| WLAN | Wireless LAN | A LAN using Wi-Fi |
| MAN | Metropolitan Area Network | A network covering a metropolitan area |
| WAN | Wide Area Network | A network spanning large geographical areas |

The Internet is a global network of interconnected networks.

## 2. The OSI Model

The Open Systems Interconnection (OSI) model divides network communication into seven conceptual layers.

| Layer | Name | Function | Examples |
|---:|---|---|---|
| 7 | Application | Network services used by applications | HTTP, DNS, SMTP |
| 6 | Presentation | Data representation, encoding, encryption concepts | TLS-related presentation functions |
| 5 | Session | Establishes and manages communication sessions | Session management |
| 4 | Transport | End-to-end transport and port numbers | TCP, UDP |
| 3 | Network | Logical addressing and routing | IPv4, IPv6, ICMP |
| 2 | Data Link | Local network delivery using frames and MAC addresses | Ethernet, Wi-Fi |
| 1 | Physical | Transmission of bits over a physical medium | Cables, radio signals |

**Important:** Real-world protocols do not always map perfectly to a single OSI layer. The model is primarily a learning and troubleshooting framework.

### Why the OSI Model Matters in Cybersecurity

- Layer 2: Investigate MAC addresses, ARP, and local network activity.
- Layer 3: Examine IP addresses, routing, and suspicious connections.
- Layer 4: Investigate TCP/UDP ports, connection attempts, and scans.
- Layer 7: Analyze application requests, DNS queries, and HTTP activity.

## 3. The TCP/IP Model

The TCP/IP model describes the protocol architecture used by the Internet.

| TCP/IP Layer | Examples |
|---|---|
| Application | HTTP, HTTPS, DNS, DHCP, SSH |
| Transport | TCP, UDP |
| Internet | IPv4, IPv6, ICMP |
| Network Access / Link | Ethernet, Wi-Fi |

The four-layer model groups several OSI functions together.

## 4. IP Addressing

An Internet Protocol (IP) address is a logical address used to identify a network interface and route packets between networks.

There are two principal IP versions:

- **IPv4:** 32-bit addresses.
- **IPv6:** 128-bit addresses.

### IPv4 Address Format

An IPv4 address consists of 32 bits, commonly represented as four decimal octets separated by dots.

Example:

```text
192.168.1.10
```

Each octet ranges from 0 to 255.

Binary representation:

```text
192      .168      .1        .10
11000000.10101000.00000001.00001010
```

Each octet contains eight bits, giving a total of 32 bits.

### Network ID and Host ID

An IPv4 address and its subnet mask determine which bits identify the network and which bits identify the host.

Example:

```text
IP address: 192.168.1.10
Subnet mask: 255.255.255.0
CIDR: /24
Network address: 192.168.1.0
Broadcast: 192.168.1.255
Usable host range: 192.168.1.1–192.168.1.254
```

This example assumes a conventional IPv4 `/24` subnet.

- **Network address:** Identifies the subnet.
- **Host address:** Identifies an interface within the subnet.
- **Broadcast address:** Sends traffic to all hosts on an IPv4 subnet that supports broadcast.

## 5. Public and Private IP Addresses

### Private IPv4 Ranges

The following IPv4 blocks are reserved for private networks under RFC 1918.

| CIDR | Address Range |
|---|---|
| `10.0.0.0/8` | 10.0.0.0 – 10.255.255.255 |
| `172.16.0.0/12` | 172.16.0.0 – 172.31.255.255 |
| `192.168.0.0/16` | 192.168.0.0 – 192.168.255.255 |

Private IP addresses are commonly used in home networks, enterprises, and virtual machines.

### Public IP Address

A public IP address is globally routable, subject to routing and allocation policies. Public addresses are commonly used for Internet-facing services.

**Important:** Not every address outside the private ranges is necessarily a usable public address. Other ranges are reserved for loopback, link-local, documentation, multicast, and special purposes.

### Other Important IPv4 Addresses

| Range / Address | Purpose |
|---|---|
| `127.0.0.0/8` | IPv4 loopback |
| `127.0.0.1` | Common loopback address |
| `169.254.0.0/16` | IPv4 link-local |
| `0.0.0.0` | Unspecified address; meaning depends on context |
| `255.255.255.255` | Limited broadcast |
| `224.0.0.0/4` | IPv4 multicast |

## 6. Subnet Masks and CIDR

A subnet mask separates the network portion of an IPv4 address from the host portion.

CIDR stands for Classless Inter-Domain Routing. Notation such as `/24` indicates the number of leading network bits.

### Common Subnet Sizes

| CIDR | Subnet Mask | Total Addresses | Typical Usable Hosts |
|---|---|---:|---:|
| `/8` | 255.0.0.0 | 16,777,216 | 16,777,214 |
| `/16` | 255.255.0.0 | 65,536 | 65,534 |
| `/24` | 255.255.255.0 | 256 | 254 |
| `/25` | 255.255.255.128 | 128 | 126 |
| `/26` | 255.255.255.192 | 64 | 62 |
| `/27` | 255.255.255.224 | 32 | 30 |
| `/28` | 255.255.255.240 | 16 | 14 |
| `/29` | 255.255.255.248 | 8 | 6 |
| `/30` | 255.255.255.252 | 4 | 2 |
| `/32` | 255.255.255.255 | 1 | 1 address |

For ordinary IPv4 subnets, the usual usable-host calculation is:

`Usable hosts = 2^(32 − prefix length) − 2`

The conventional subtraction accounts for the network and broadcast addresses. Special cases, including `/31` point-to-point links and `/32` host routes, do not follow this ordinary calculation.

### Subnetting Example

Given:

```text
IP address: 192.168.1.70/26
```

A `/26` subnet has 64 total addresses.

The subnet boundaries in the last octet are 0, 64, 128, and 192.

Therefore:

```text
Network address: 192.168.1.64
Broadcast address: 192.168.1.127
Usable host range: 192.168.1.65–192.168.1.126
Total addresses: 64
Usable hosts: 62
```

Subnetting is important for understanding network segmentation, firewall rules, routing, and the scope of network investigations.

## 7. MAC Addresses and ARP

### MAC Address

A Media Access Control (MAC) address is a link-layer identifier used for communication on local networks.

A commonly displayed Ethernet MAC address is 48 bits long.

Example:

```text
00:1A:2B:3C:4D:5E
```

IP addresses support logical addressing and routing, while MAC addresses are used for local link delivery. A MAC address can be changed or spoofed in some circumstances, so it should not be treated as definitive proof of a device's identity.

### ARP — Address Resolution Protocol

ARP is used on IPv4 local networks to resolve an IPv4 address to a link-layer address.

Typical process:

1. A host needs to send a packet to another host on its local IPv4 network.
2. It checks its ARP cache.
3. If the mapping is unavailable, it may broadcast an ARP request.
4. The relevant host replies with its MAC address.
5. The sender can use that mapping to build the Ethernet frame.

When the destination is on a different subnet, the sender typically resolves the MAC address of its default gateway instead.

**Security relevance:** Unexpected ARP replies, conflicting IP-to-MAC mappings, and unusual ARP traffic may be indicators of ARP spoofing or other local network issues. Investigate them alongside other evidence.

## 8. TCP and UDP

### TCP — Transmission Control Protocol

TCP is a connection-oriented transport protocol that provides a reliable, ordered byte stream.

Key characteristics:
- Establishes a connection before data transfer.
- Uses sequence numbers and acknowledgments.
- Retransmits data when required.
- Provides flow control and congestion control.

#### TCP Three-Way Handshake

```text
Client                         Server
  |                               |
  | -------- SYN ---------------> |
  | <----- SYN + ACK ------------ |
  | -------- ACK ---------------> |
  |                               |
  |       Connection established  |
```

The handshake establishes the TCP connection. It does not by itself prove that an application login or other transaction succeeded.

### UDP — User Datagram Protocol

UDP is a connectionless transport protocol that sends datagrams without TCP's built-in reliability and ordering guarantees.

Common uses include:
- DNS queries.
- Real-time voice and video.
- Streaming and gaming traffic.
- DHCP.
- Some VPN and tunneling protocols.

### TCP vs UDP

| Feature | TCP | UDP |
|---|---|---|
| Connection setup | Yes | No transport handshake |
| Built-in reliable delivery | Yes | No |
| Ordered byte stream | Yes | No |
| Protocol overhead | Generally higher | Generally lower |
| Common uses | HTTPS, SSH, email | DNS, DHCP, real-time traffic |

UDP applications can implement their own reliability mechanisms when needed.

## 9. Common Network Ports

A port identifies a transport-layer endpoint used by an application or service. TCP and UDP have separate port spaces.

| Port | Protocol / Service | Typical Use |
|---:|---|---|
| 20/21 | FTP | File transfer |
| 22 | SSH | Secure remote administration |
| 23 | Telnet | Unencrypted remote terminal |
| 25 | SMTP | Email transfer |
| 53 | DNS | Domain name resolution |
| 67/68 | DHCP | IPv4 address configuration |
| 80 | HTTP | Web traffic |
| 110 | POP3 | Email retrieval |
| 123 | NTP | Time synchronization |
| 143 | IMAP | Email access |
| 161/162 | SNMP | Network management |
| 389 | LDAP | Directory services |
| 443 | HTTPS | HTTP over TLS |
| 445 | SMB | Windows file sharing |
| 465/587 | SMTP over TLS / message submission | Email submission |
| 514 | Syslog | System logging, commonly UDP |
| 636 | LDAPS | LDAP over TLS |
| 993 | IMAPS | IMAP over TLS |
| 995 | POP3S | POP3 over TLS |
| 1433 | Microsoft SQL Server | Database access |
| 3306 | MySQL | Database access |
| 3389 | RDP | Remote Desktop |
| 5432 | PostgreSQL | Database access |
| 5900 | VNC | Remote desktop access |

These are common associations, not guarantees. Services can run on nonstandard ports, and a port number alone does not prove which application is using it.

### Port Number Ranges

- **0–1023:** System ports, traditionally called well-known ports.
- **1024–49151:** User or registered ports.
- **49152–65535:** Dynamic/private ports.

These ranges describe the IANA port registry conventions. Operating systems may use different ephemeral-port allocation ranges.

## 10. DNS — Domain Name System

DNS translates domain names into information used by network clients, including IP addresses.

Example:

```text
example.com → IP address
```

### Common DNS Record Types

| Record | Purpose |
|---|---|
| A | Maps a name to an IPv4 address |
| AAAA | Maps a name to an IPv6 address |
| CNAME | Alias for another domain name |
| MX | Identifies mail servers |
| NS | Identifies authoritative name servers |
| TXT | Stores text data, often used for verification and email security |
| PTR | Supports reverse DNS lookups |
| SOA | Contains zone authority and administrative information |

### DNS Resolution Process

1. A client needs to resolve a domain name.
2. It checks relevant local caches and resolver configuration.
3. A recursive resolver obtains the answer from its cache or queries DNS servers as necessary.
4. The answer is returned to the client and may be cached.

### Cybersecurity Relevance

DNS investigations can reveal:
- Connections to suspicious domains.
- Domain generation algorithm (DGA) activity.
- Possible command-and-control communication.
- DNS tunneling indicators.
- Unusual query frequency or record types.

A suspicious DNS query is an investigative lead, not proof of compromise.

## 11. DHCP — Dynamic Host Configuration Protocol

DHCP automatically provides network configuration to clients, commonly including an IP address, subnet mask or prefix, default gateway, and DNS resolver information.

### DHCP DORA Process

```text
Discover → Offer → Request → Acknowledge
```

- **Discover:** Client looks for DHCP servers.
- **Offer:** Server offers configuration.
- **Request:** Client requests an offered configuration.
- **Acknowledge:** Server confirms the lease.

DHCP commonly uses UDP ports 67 and 68 for IPv4.

**Security relevance:** Unexpected DHCP servers, suspicious configuration changes, or unfamiliar leases may indicate misconfiguration or rogue DHCP activity.

## 12. HTTP, HTTPS, and TLS

### HTTP

Hypertext Transfer Protocol is an application-layer protocol used to exchange web requests and responses.

Common methods include:
- `GET` — retrieve a representation.
- `POST` — submit data for processing.
- `PUT` — create or replace a resource at a target URI, depending on application behavior.
- `DELETE` — request resource deletion.

HTTP status codes are grouped into five classes:

| Range | Meaning |
|---|---|
| 1xx | Informational |
| 2xx | Success |
| 3xx | Redirection |
| 4xx | Client error |
| 5xx | Server error |

### HTTPS

HTTPS is HTTP protected by TLS. TLS helps provide confidentiality, integrity, and server authentication when correctly configured and validated.

HTTPS does not make a website automatically trustworthy, nor does it guarantee that every aspect of an application is secure.

### Security Relevance

When analyzing web traffic, examine:
- Requested hostnames and URLs when available.
- HTTP methods and status codes.
- User-Agent values.
- Redirect chains.
- Certificate information.
- Connection timing and destination IPs.
- Unusual request patterns and data volumes.

Encrypted traffic may limit visibility into application contents, but metadata and connection patterns can still be useful.

## 13. ICMP and Network Diagnostics

Internet Control Message Protocol (ICMP) supports error reporting and diagnostic functions for IP networks.

The `ping` utility commonly uses ICMP Echo Request and Echo Reply messages.

Example:

```bash
ping 192.168.1.1
```

A successful reply indicates that the target responded to the probe. A failed reply does not necessarily mean the host is offline; a firewall, routing issue, or disabled response may explain it.

### Traceroute

Traceroute tools help identify the sequence of network hops toward a destination.

Linux:

```bash
traceroute example.com
```

Windows:

```cmd
tracert example.com
```

Some networks filter or deprioritize diagnostic traffic, so intermediate hops may not respond even when connectivity works.

## 14. Routing, Gateways, and NAT

### Router

A router forwards IP packets between networks using routing information.

### Default Gateway

A default gateway is the next hop used when a destination does not match a more specific route in the routing table.

### NAT — Network Address Translation

NAT modifies IP address information in packets as they pass through a translating device.

A common home-network setup uses Network Address and Port Translation (NAPT/PAT) to allow multiple private-addressed devices to share a public IPv4 address.

NAT is not a substitute for a firewall or a complete security control.

### VPN — Virtual Private Network

A VPN creates a protected logical connection over an underlying network. Depending on its design, it can provide encryption, authentication, and access to remote networks.

VPN use does not guarantee anonymity or complete protection from malware, phishing, or compromised endpoints.

## 15. Common Networking Tools

### Linux

```bash
ip addr
ip route
ip neigh
ss -tulnp
ping 192.168.1.1
traceroute example.com
dig example.com
nslookup example.com
curl -I https://example.com
```

| Command | Purpose |
|---|---|
| `ip addr` | Shows network interfaces and addresses |
| `ip route` | Displays the routing table |
| `ip neigh` | Shows neighbor-cache entries |
| `ss -tulnp` | Displays listening sockets; process details may require elevated privileges |
| `ping` | Tests ICMP reachability |
| `traceroute` | Examines the route toward a destination |
| `dig` | Queries DNS |
| `nslookup` | Performs DNS lookups |
| `curl -I` | Requests HTTP response headers using a HEAD request when supported |

### Windows

```cmd
ipconfig /all
route print
arp -a
netstat -ano
ping 192.168.1.1
tracert example.com
nslookup example.com
```

| Command | Purpose |
|---|---|
| `ipconfig /all` | Displays detailed network configuration |
| `route print` | Shows the routing table |
| `arp -a` | Displays the ARP cache |
| `netstat -ano` | Shows connections and listening ports, including associated process IDs |
| `ping` | Tests ICMP reachability |
| `tracert` | Traces the route toward a destination |
| `nslookup` | Queries DNS |

Use these commands on systems you own or are authorized to investigate. Network visibility depends on permissions, operating-system version, and configuration.

## 16. Wireshark for Packet Analysis

Wireshark is a network protocol analyzer used to inspect captured packets.

### Basic Workflow

1. Open Wireshark and select an authorized network interface or an existing capture file.
2. Start or load a capture.
3. Inspect packet timestamps, source and destination addresses, protocols, and lengths.
4. Expand protocol fields to examine packet details.
5. Apply display filters to isolate relevant traffic.
6. Follow streams when appropriate and correlate findings with other evidence.
7. Save the capture and document observations when conducting an investigation.

### Useful Wireshark Display Filters

| Filter | Purpose |
|---|---|
| `dns` | DNS traffic |
| `http` | HTTP traffic |
| `tcp` | TCP packets |
| `udp` | UDP packets |
| `icmp` | ICMP packets |
| `ip.addr == 192.168.1.10` | Packets involving an IPv4 address |
| `ip.src == 192.168.1.10` | Packets originating from an IPv4 address |
| `ip.dst == 192.168.1.10` | Packets destined for an IPv4 address |
| `tcp.port == 443` | TCP packets with source or destination port 443 |
| `tcp.flags.syn == 1` | TCP packets with the SYN flag set |
| `tcp.analysis.retransmission` | TCP packets identified as retransmissions |
| `http.request` | HTTP requests recognized by Wireshark |

**Capture filter vs display filter:**

- Capture filters control which packets are captured.
- Display filters control which captured packets are shown in the packet list.

A display filter does not delete the hidden packets from the capture file.

For example, a capture filter might use `tcp port 443`, while a display filter uses `tcp.port == 443`.

## 17. Networking in SOC and DFIR Investigations

Network evidence is often used to reconstruct an incident timeline and understand communications between a suspected compromised system and other hosts.

### Important Questions for an Investigation

- Which internal and external IP addresses communicated?
- Which ports and protocols were involved?
- Was there a DNS query shortly before a suspicious connection?
- Did a host make repeated outbound connections?
- Were there unusual amounts of outbound data?
- Did the activity involve remote administration or file-sharing services?
- Do firewall, proxy, DNS, endpoint, and packet-capture logs support the same timeline?

### Potential Indicators of Suspicious Activity

- Repeated connections to unusual destinations.
- Unexpected outbound traffic on uncommon ports.
- Periodic connections that may indicate automated beaconing.
- DNS queries for suspicious or newly observed domains.
- Unusual SMB or RDP activity between internal systems.
- Large outbound transfers inconsistent with normal behavior.
- Repeated connection attempts to many ports or hosts.

These patterns are not conclusive on their own. Investigators should validate findings using endpoint artifacts, authentication logs, threat intelligence, and other available evidence.

### Basic Network Investigation Workflow

1. Identify the affected host and investigation time window.
2. Collect authorized logs and packet captures.
3. Establish the host's IP address, gateway, DNS configuration, and relevant network context.
4. Identify source and destination IPs, ports, protocols, and timestamps.
5. Review DNS queries and associated connections.
6. Look for repeated patterns, unusual destinations, and unexpected internal communications.
7. Correlate network findings with endpoint events and user activity.
8. Record evidence, timestamps, investigative methods, and confidence levels.

## 18. Recommended Learning Resources

The following sources provide authoritative specifications and practical documentation.

1. **RFC 791 — Internet Protocol (IPv4):** https://www.rfc-editor.org/rfc/rfc791
2. **RFC 1918 — Private IPv4 Address Allocation:** https://www.rfc-editor.org/rfc/rfc1918
3. **RFC 9293 — Transmission Control Protocol (TCP):** https://www.rfc-editor.org/rfc/rfc9293
4. **RFC 768 — User Datagram Protocol (UDP):** https://www.rfc-editor.org/rfc/rfc768
5. **RFC 1034 — Domain Names: Concepts and Facilities:** https://www.rfc-editor.org/rfc/rfc1034
6. **IANA Service Name and Transport Protocol Port Number Registry:** https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml
7. **Wireshark User's Guide:** https://www.wireshark.org/docs/wsug_html/
8. **Wireshark Display Filter Reference:** https://www.wireshark.org/docs/dfref/

---

*Purpose: Cybersecurity study notes covering networking fundamentals, SOC analysis, and digital forensics. Verify protocol-specific details against the relevant standards and tool documentation when conducting real investigations.*
