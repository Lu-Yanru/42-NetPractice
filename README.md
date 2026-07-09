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
- [GeeksforGeeks Difference between router and switch](https://www.geeksforgeeks.org/computer-networks/difference-between-router-and-switch/)
- [GeeksforGeeks Layers of OSI model](https://www.geeksforgeeks.org/computer-networks/open-systems-interconnection-model-osi/)

AI is used to explain network related concepts in simple language with concrete examples.

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
- Each host bit (bits set to 0) can be used to create an IP address in that network and be assigned to a host. The number of possible hosts in a network is 2^(number of 0 bits in the subnet mask).
For example, `255.255.255.0` (or `11111111.11111111.11111111.00000000`) means the first three octets represents the network and are fixed, but the last octet can be anything between 0 and 255. There are 8 host bits in the subnet mask, so there can be max 256 (- 2 for network and broadcast addresses) hosts in the network.

**Subnetting** is dividing a large network into smaller subnetworks (subnets) by changing the subnet mask to suit the need of how many hosts are needed in a network, so the IP addrees space can be used more efficiently. Steps to subnet:
1. Calculate how many host bits you need to hack (change from host bits to network bits) using the following chart:

|Number of bits to hack | 8 | 7| 6| 5 | 4| 3 | 2| 1|
|----|---|--|--|---|--|---|--|--|
|Number of networks|256 | 128 | 64 | 32 | 16 | 8 | 4 | 2|

For example, if you need 4 subnets, you need to convert 2 bits from host bits to network bits, i.e. `11111111.11111111.11111111.00000000` -> `11111111.11111111.11111111.11000000`.

2. Find the increment, i.e. the decimal number to divide the subnets, which is the last network bit. In the example, it is 64.

This means the IP address ranges of the subnets are:
- 192.168.1.0 - 192.168.1.63
- 192.168.1.64 - 192.168.1.127
- 192.168.1.128 - 192.168.1.191
- 192.168.1.192 - 192.168.1.255

#### CIDR notation
The **Classless Inter-Domain Routing (CIDR) notation** represents how many bits are in the network mask as a slash and a decimal number. For example `192.168.1.0/24` means there are 24 bits in the network mask (`255.255.255.0`).

### Default gateways
A **default gateway** is a node in a network (typically a router) that serves as an access point to another network.
Hosts need to go through the default gateway when when communicating with devices that are not in the same network.
It assigns IP addresses to hosts in the network,
and also has an IP address itself.

### Routers and switches
A **router** is a computer and networking device that forwards data packets between computer networks.

A **network switch** is networking hardware that connects devices on a computer network by using packet switching to receive and forward data to the destination device.

A switch connects devices within the same local network and forwards traffic using MAC addresses.
A router connects different networks together and forwards traddic using IP addresses.

### OSI layers
The **Open System Interconnection (OSI) Model** is a conceptual framework created by the International Organization for Standardization (ISO) to describe how data is transmitted across a network using a structured seven-layer architecture.
- Layer 1: Physical layer: Establishes physical connection between devices and transmits raw bits over the medium.
- Layer 2: Data link layer: Provides node-to-node delivery and error detection/correction.
- Layer 3: Network layer: Handles logical addressing and routing of data between different networks.
- Layer 4: Transport layer: Ensures end-to-end communication, segmentation, flow control, and error handling.
- Layer 5: Session layer: Establishes, manages, and terminates communication sessions between applications.
- Layer 6: Presentation layer: Translates, encrypts, and formats data for the application layer.
- Layer 7: Application layer: Provides network services directly to end-user applications.
