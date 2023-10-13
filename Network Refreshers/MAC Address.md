# MAC Address Cheat Sheet

## MAC Address Basics:

A MAC address is a unique identifier assigned to a network interface card (NIC) or network adapter.
MAC addresses are 48 bits (6 bytes) or 64 bits (8 bytes) in length, depending on the type.
MAC addresses are typically represented as a series of six or eight hexadecimal digits separated by colons or hyphens (e.g., 00:1A:2B:3C:4D:5E).
MAC addresses are used at the data link layer (Layer 2) of the OSI model to identify devices on a local network.

## Types of MAC Addresses:

### Unicast MAC Address:

Identifies a specific network interface.
The least significant bit of the first byte is set to 0 (e.g., 00:1A:2B:3C:4D:5E).

### Multicast MAC Address:

Identifies a group of network interfaces.
The least significant bit of the first byte is set to 1 (e.g., 01:1A:2B:3C:4D:5E).

### Broadcast MAC Address:

Sent to all devices on the local network.
All bits are set to 1 (e.g., FF:FF:FF:FF:FF:FF).

## MAC Address Formats:

### EUI-48 (Extended Unique Identifier - 48 bits):

Used in most Ethernet networks.
Consists of 48 bits divided into two parts: Organizationally Unique Identifier (OUI) and device-specific identifier.
OUI is assigned to manufacturers by the IEEE.

### EUI-64 (Extended Unique Identifier - 64 bits):

Used in IPv6 addressing.
Consists of 64 bits and includes a 24-bit OUI.

## Finding MAC Addresses:

To find the MAC address of a device:
On Windows: Use ipconfig /all or check the network adapter properties.
On Linux/Unix: Use ifconfig or ip addr commands.
On macOS: Use ifconfig or networksetup -listallhardwareports.
On routers: Check the DHCP client list or ARP table.

## Changing MAC Addresses:

You can change a device's MAC address (MAC spoofing) for privacy or security reasons.
Use tools like ifconfig (Linux/Unix) or device-specific utilities on Windows and macOS.


## MAC Address Filtering:

Routers and network switches can use MAC address filtering to control which devices can access the network.

## MAC Address and ARP:

ARP (Address Resolution Protocol) maps IP addresses to MAC addresses on local networks.

## IEEE Registration Authority:

The IEEE maintains the registration authority responsible for OUI assignment.
The OUI identifies the manufacturer or organization that produced the NIC.

## Vendor Lookup:

You can use online tools or databases to look up the manufacturer associated with an OUI.
https://macvendors.com/

## MAC Address Security:

MAC addresses are not secure by themselves and can be easily spoofed.
Network security relies on higher-layer protocols (e.g., WPA2/3 for Wi-Fi) and authentication methods.