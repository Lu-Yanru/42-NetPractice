*This project has been created as part of the 42 curriculum by yanlu.*

# NetPractice

## Description
This project introduces the basics of computer networking, including how to configure IP addresses, connect devices through a router, and understand the role of a gateway within a network.

## Instructions

Run the project by:
- Download the file attached to the project's page and extract it.
- In the extracted folder, run the `run.sh` file. This shell script will launch a web server and open the project page on a web browser.
- After completing a level, click the `Get my config` button to export the configuration file.

### Submission details
10 exported configuration files (one per level) are submitted at the repository root.

## Resources
- [YouTube series on network and subnetting by NetworkChuck](https://www.youtube.com/watch?v=5WfiTHiU4x8&list=PLIhvC56v63IKrRHh3gvZZBAGvsvOhwrRF)
- Master OccupytheWeb. 2023. *Network basics for hackers: How networks work and how they break.* https://hackers-arise.com/getting-started/network-basics-for-hackers/

### TCP/IP addressing
**TCP/IP** (the internet protocol suite) are protocols that define the way to communicate in the internet and similar computer networks.

**The Internet Protocol (IP)** is the protocol used to define the source and destination IP address of a packet as it traverse the internet.
It is often used in conjunction with the **Transmission Control Protocol (TCP)**, which provides reliable, ordered, and error-checked delivery of a stream of octets (bytes) between applications running on hosts communicating via an IP network.

An **IP address** is a unique identifying series of numbers assigned to every device connected to the internet, so that the devices can communicate with each other.

An IP version 4 (IPv4) address consists of four octets (4 * 8 = 32 bits) in decimal notation separated by periods, e.g. `192.168.1.101`. This means that each number can be betwenn 0 and 255.

The first three octets are the network portion of the IP address, which identifies a specific network. The last octet is the host portion, which identifies individual devices in that network. For the host portion, usually 0 is reserved for the network address and 255 is reserved for the broadcast address.

There are five classes of IP address:
- Class A: 1.0.0.0 - 126.255.255.255 (default subnet mask 255.0.0.0)
- Class B: 128.0.0.0 - 191.255.0.0 (default subnet mask 255.255.0.0)
- Class C: 192.0.0.0 - 223.255.255.0 (default subnet mask 255.255.255.0)
- Class D: 224.0.0.0 - 239.255.255.255
- Calss E: 240.0.0.0 - 255.255.255.255
Class A - C are unicast (one-to-one transmission) addresses.
Class A allows more hosts per network, while class C allows many networks but fewer hosts per network.
Therefore, nowadays, we usually use classless networks by dividing a class A network into smaller subnetworks to make use of more of the IP address range.
Class D is for multicast (one-to-many or many-to-many transmission) networking and class E is for experimental purposes.
127.0.0.0 are loop back addresses used for network testing.

#### Public vs. private IP addresses
**Public IP addresses** are IP addresses that can be reached on the internet and are unique.
**Private IP addresses** are not unique, but not directly connected to the internet and has to be translated by the router to a public IP address using **Network Address Translation (NAT)**.
- Class A: 10.0.0.0 - 10.255.255.255 (subnet mask 255.0.0.0)
- Class B: 172.16.0.0 - 172.31.255.255 (subnet mask 255.255.0.0)
- Class C: 192.168.0.0 - 192.168.255.255 (subnet mask 255.255.255.0)

### Subnet masks
The **subnet mask** has the same 32-bit structure as the IP address and is used to distinguish the network bits from the host bits.
- The network bits (bits set to 1) are the part of the IP address that will not change, so it tells us which network we are on.
- Each host bit (bits set to 0) can be used to create an IP address in that network and be assigned to a host.
For example, `255.255.255.0` (or `11111111.11111111.11111111.00000000`) means the first three octets represents the network and are fixed, but the last octet can be anything btween 0 and 255, depending on what device it is assigned to.

**Subnetting** is dividing a large network into smaller subnetworks (subnets) by changing the subnet mask to suit the need of how many hosts are needed in a network, so the IP addrees space can be used more efficiently.

### Default gateways
or default router or router
assigns ip address in the network.
also has an ip address itself.
needs to go through when when communicating with devices that are not in the same network

### Routers and switches

### OSI layers
