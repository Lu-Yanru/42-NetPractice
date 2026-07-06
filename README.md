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
- [YouTube series on network by NetworkChuck](https://www.youtube.com/watch?v=5WfiTHiU4x8&list=PLIhvC56v63IKrRHh3gvZZBAGvsvOhwrRF)
- Master OccupytheWeb. 2023. *Network basics for hackers: How networks work and how they break.* https://hackers-arise.com/getting-started/network-basics-for-hackers/

### TCP/IP addressing
An **Internet Protocol (IP) address** is a unique identifying series of numbers assigned to every device connected to the internet, so that the devices can communicate with each other.

An IP version 4 (IPv4) address consists of four octets (4 * 8 = 32 bits) in decimal notation separated by periods, e.g. `192.168.1.101`. This means that each number can be betwenn 0 and 255.

The first three octets are the network portion of the IP address, which identifies a specific network. The last octet is the host portion, which identifies individual devices in that network. For the host portion, usually 0 is reserved for the network address and 255 is reserved for the broadcast address.

### Subnet masks
or Netmask
also consists of four dot-separated octets corresponding to the IP address.
`255.255.255.0` means the first 3 numbers in the local network is fixed but the last number can be anything btween 0 and 255, depending on what device it's assigned to.

### Default gateways
or default router or router
assigns ip address in the network.
also has an ip address itself.
needs to go through when when communicating with devices that are not in the same network

### Routers and switches

### OSI layers
