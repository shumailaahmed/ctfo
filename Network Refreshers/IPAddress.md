# IP Address Cheat Sheet

IP address are layer 3, related to routing.
## IP Address Types:

### IPv4 (Internet Protocol Version 4):

Consists of 32 bits.
Format: A.B.C.D (e.g., 192.168.1.1).
Addresses are typically written in decimal format.
Commonly used for most internet communication.

### IPv6 (Internet Protocol Version 6):

Consists of 128 bits.
Format: 8 groups of four hexadecimal digits separated by colons (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334).
Designed to address IPv4 exhaustion and provide more addresses.

## IP Address Classes (IPv4):

### Class A:

Range: 1.0.0.0 to 126.0.0.0
Leading bit: 0
Subnet mask: 255.0.0.0
Supports 16 million hosts.

### Class B:

Range: 128.0.0.0 to 191.255.0.0
Leading bits: 10
Subnet mask: 255.255.0.0
Supports 65,000 hosts.

### Class C:

Range: 192.0.0.0 to 223.255.255.0
Leading bits: 110
Subnet mask: 255.255.255.0
Supports 254 hosts.

### Class D (Multicast):

Range: 224.0.0.0 to 239.255.255.255
Leading bits: 1110
Used for multicast groups.

### Class E (Experimental):

Range: 240.0.0.0 to 255.255.255.255
Leading bits: 1111
Reserved for experimental use.

## IP Address Reserved Ranges:

### Loopback Address:

IPv4: 127.0.0.1
IPv6: ::1
Used for testing network connectivity on the local machine.

### Private IP Addresses (IPv4):

Class A: 10.0.0.0 to 10.255.255.255
Class B: 172.16.0.0 to 172.31.255.255
Class C: 192.168.0.0 to 192.168.255.255
Used for internal, private networks.

### Link-Local Addresses (IPv4):

Range: 169.254.0.0 to 169.254.255.255
Used when no DHCP server is available (Autoconfiguration).

### CIDR (Classless Inter-Domain Routing):

Format: A.B.C.D/x (e.g., 192.168.1.0/24)
Combines multiple IP addresses into a single prefix.
"/x" represents the subnet mask length (e.g., /24 means 24 bits are network, and 8 bits are host).

## Special IP Addresses:

### Broadcast Address (IPv4):

Address where data is sent to all hosts on the network.
Example: 192.168.1.255

### Network Address (IPv4):

Address representing the entire network.
Example: 192.168.1.0

### Default Gateway:

The router's IP address used to access external networks.

### Public IP Address:

IP address assigned to a device on the public internet.

### Dynamic Host Configuration Protocol (DHCP):

Protocol used to automatically assign IP addresses to devices on a network.

### Subnet Mask:

Defines the network and host portions of an IP address.


### DNS (Domain Name System):

Converts domain names into IP addresses.

