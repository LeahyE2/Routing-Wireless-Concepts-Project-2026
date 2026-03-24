# Routing-Wireless-Concepts-Project-2026
# Description:
Aurora Healthcare Group, a growing Irish private healthcare provider operating clinics and
day-surgery centres, has tasked you with designing and implementing a secure and efficient
LAN-based internetwork. The organisation operates from a main Central Campus in
Dublin and has two regional clinics located in Limerick and Sligo. Each location requires
seamless communication, strong local security controls (especially at Layer 2), and
scalability to support future expansion of services and staff.
Your role is to create a prototype network that fulfils the company’s requirements and
addresses potential vulnerabilities on the LAN segments. This prototype will be presented to
Aurora Healthcare Group along with a detailed report explaining the design decisions,
network features and how the requirements are met.
This project will give you experience in designing Local Area Networks (LANs), configuring
VLANs, addressing LAN security vulnerabilities, implementing IP address allocation and
setting up inter-site communication. It will also challenge you to think critically about
network scalability, security and reliability in a healthcare environment

## Requirements:
# Requirement 1 – VLAN Design at Central Campus
The Dublin Central Campus must include two separate VLANs to segment network traffic
and improve performance and security:
 Clinical VLAN (VLAN 100) for 110 users (doctors, nurses and clinical staff).
 Admin VLAN (VLAN 200) for 25 users (HR, finance, management).
End users in the two VLANs should be able to communicate with each other as needed (for
example, clinical staff accessing admin systems), using inter-VLAN routing configured on the
Central Campus router or a multi-layer switch.
VLANs are not required for the Limerick and Sligo clinics, which will operate with simpler flat
LANs. The segmentation provided by VLANs is specific to the Central Campus to support its
larger and more complex operational structure.

# Requirement 2 – IP Addressing and DHCP
Each VLAN at the Central Campus must have its own unique IPv4 address range that clearly
reflects the VLAN number, with dynamic addressing via a DHCP server at the Central
Campus. Choose appropriate default gateways on the inter-VLAN routing device.
Central Campus – Clinical VLAN (VLAN 100):
 IP Address Range: 10.10.100.0/25
 Network Address: 10.10.100.0
 Broadcast Address: 10.10.100.127
 Usable Host Range: 10.10.100.1 – 10.10.100.126
Central Campus – Admin VLAN (VLAN 200):
 IP Address Range: 10.10.200.0/27
 Network Address: 10.10.200.0
 Broadcast Address: 10.10.200.31
 Usable Host Range: 10.10.200.1 – 10.10.200.30
Each regional clinic requires its own IPv4 address allocation with at least 30 usable IP
addresses, dynamically assigned by a local DHCP service running on its edge routing
device (the branch router/MLS acts as the DHCP server for that site):
Limerick Clinic IPv4 Network:
 IP Address Range: 172.16.10.0/27
 Network Address: 172.16.10.0
 Broadcast Address: 172.16.10.31
 Usable Host Range: 172.16.10.1 – 172.16.10.30
Sligo Clinic IPv4 Network:
 IP Address Range: 172.16.20.0/27
 Network Address: 172.16.20.0
 Broadcast Address: 172.16.20.31
 Usable Host Range: 172.16.20.1 – 172.16.20.30

# Requirement 3 – LAN Layer 2 Security at Central Campus
The Central Campus LAN must implement Layer 2 security measures on the switches to
mitigate the following vulnerabilities:
 MAC Table Attacks: Prevent attackers from flooding the switch MAC address
table (e.g. using port security).
 VLAN Attacks: Protect against VLAN hopping and double-tagging to ensure
VLAN segmentation is not bypassed.
 STP Attacks: Safeguard the spanning tree topology from malicious BPDUs
that could cause loops or force a rogue root bridge.
 DHCP Attacks: Mitigate DHCP starvation and rogue DHCP servers to prevent
denial of service or unauthorised configurations.
 ARP Spoofing: Address ARP spoofing to prevent attackers from impersonating
devices and intercepting traffic.
# Requirement 4 – Secure Remote Administration
Ensure the Central Campus edge routing device (Router or MLS) is remotely accessible
by two network administrators using SSH with local authentication. Create two local user
accounts with different privilege levels and ensure that remote access via Telnet is disabled.
# Requirement 5 – Static and Floating Static Routing Between Sites
Configure static routes to enable communication between:
 Central Campus and Limerick Clinic
 Central Campus and Sligo Clinic
 Limerick and Sligo Clinics (via the Central Campus or via an intermediate WAN
router, as per your topology)
The Central Campus and clinics will not be connected to the same router, therefore static
routes will be required on the relevant routers to connect the remote networks.
In addition, you must configure floating static routes as backup routes on the appropriate
routers. These floating static routes should provide an alternative path between the Central
Campus and each clinic (and/or between clinics) in the event of a primary WAN link failure.
You should clearly identify in your design and documentation which links are primary and
which are backup, and how the floating static routes support resilience and failover. 
