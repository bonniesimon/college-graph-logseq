- Syllabus
	- Internet Control Protocols – ICMP, ARP, RARP, BOOTP.
	- Internet Multicasting – IGMP, Exterior Routing Protocols – BGP.
	- IPv6 – Addressing – Issues, ICMPv6.
# Internet Control Protocols
	- source
		- Tanenbaum
		- Behrouz
	- In addition to IP, which is used for data transfer, the internet has several companion control protocols that are used in the network layer.
	- ## ICMP - Internet Control Message Protocol
		- ICMP is an error reporting protocol for IP
		- When a network problem is encountered, ICMP does not correct it; it merely reports the problem.
			- When datagram delivery errors occur, ICMP is used to report these errors back to the source of the datagram.
		- ICMP is also used to test the internet.
		- It does not propagate information about the network changes to routers.
		- Different types of ICMP messages defined
			- Each ICMP message type is carried encapsulated in an IP packet.
			-
			  |       Message Type      |               Description               |
			  |:-----------------------:|:---------------------------------------:|
			  | Destination unreachable | Packet could not be delivered           |
			  | Time exceeded           | Time to live field hit 0                |
			  | Parameter problem       | Invalid header field                    |
			  | Source quench           | Choke packet                            |
			  | Redirect                | Teach a router about geography          |
			  | Echo request            | Ask a machine if it is alive            |
			  | Echo reply              | Yes, I am alive.                        |
			  | Timestamp request       | Same as Echo request but with timestamp |
			  | Timestamp reply         | Same as Echo reply but with timestamp   |
		- General format of ICMP message refer Ma'ams pdf
	- Address Mapping
		- The delivery of a packet to a host or a router requires two levels of addressing
			- Logical(IP address) & Physical (Ethernet or MAC) addressing.
		- Mapping Logical to Physical address (ARP)
		- Mapping Physical to Logical address (RARP)
		- How does IP address get mapped onto data link layer addresses such as Ethernet?
			- Answer in text pdf page no: 491 & also in ma'ams pdf.
			- We can use a configuration file that maps the IP addresses onto Ethernet addresses.
			- or we can use the following method.
			- Basically what happens is that say machine A wants to communicate with machine B.
			- A sends a broadcast packet onto the Ethernet asking who owns the IP address to which A has to send data
			- This broadcast arrives at every machine on the Ethernet and each one will check its IP address.
			- B will understand that it is B's IP address and respond.
			- This way A now knows that B is the one to which it needs to send data
			- The protocol used for asking this question and getting the reply is called ARP(Address Resolution Protocol)
			- The advantage of using ARP method over configuration files is that it's simple and less complex.
				- The system manager doesn't have to create a configuration file. Rather he simply needs to assign each machine an IP address and decide about subnet mask. ARP does the rest.
	- ## ARP (Address Resolution Protocol)
		- For a sender to send the IP packet, the MAC address of the destination must be know.
		- ARP is used to find this.
		- If the destination is not know, then the sender broadcasts the ARP-discovery packet requesting the MAC address of the intended destination.
		- Since it is a broadcast, all the hosts in the network will get this ARP discovery packet. But only the intended host whose IP is associated will accept the packet. Everyone else will discard it.
		- The receiver will now send a unicast packet with its MAC address (ARP-reply) to the sender of the ARP-discovery packet.
		- After the original sender receives the ARP-reply, it updates the ARP cache and start sending unicast message to the destination.
		- Proxy ARP
			- When we need to send data to a host on another network
			- Proxy is used when we want the destination host to appear as if it's on the same network as the receiver but in reality it is present in another network.
			- Say host 1 and host 2 are in one network and host 3 and host 4 are in a different network.
			- Host 1 wants to send data to host 4.
			- We keep a proxy ARP in the first network which replies to the ARP-discovery packet sent by host 1 on behave of host 4.
			- Then after host one gets the ARP-reply, it'll sent data to host 4 which is present in another network.
	- ## RARP
	- Given an Ethernet address, how to get the IP address. We can use RARP
		- A machine can use physical address to get logical address using RARP
	- A RARP message is created and broadcast on the local network
	- The machine on the network that knows the logical address responds with RARP reply.
	- Disadvantage
		- Not forwarded by routers, hence RARP server is needed on each network.
		- Solution : Bootstrap protocol, BOOTP
			- uses UDP messages, which are forwarded over routers
	- ## BOOTP
		- The protocol allows diskless machines to discover their IP address and the address of the server host.
		- Events in BOOTP
			- The client broadcasts its MAC address asking for help in booting.
			- The BOOTP server responds with the data that specifies how the client should be configured
		- Disadvantage
			- It requires manual configuration of tables mapping IP addresses to Ethernet addresses.
		- To eliminate this problem we use DHCP
	- ## DHCP (Dynamic Host Configuration Protocol)
		- Allows both manual IP address assignment and automatic assignment
		- Based on the idea of a special server that assign IP addresses to host asking for one.
		- ? working/events in DHCP
# Internet Multicasting
	- The IP protocol can be involved in two types of communication:
		- unicasting
			- Communication between one sender and one receiver
			- One to one communication
		- multicasting
			- Communication between one sender and more than one receivers
			- One to many communication
			- Eg: video on demand, multiple users can be informed about a information
			- IP supports multicasting using class D addresses
			- 2 kinds of address are supported
				- permanent address
					- always there, no setup needed
				- temporary address
					- must be created before they are used.
					- Similar to how google meet works.
					- Ask its host to join a specific group
					- ask its host to leave the group
					- last process on a host leaves, group no longer present on the group
			- IGMP (Internet Group Management Protocol) is used for multicasting.
	- ## IGMP (Internet Group Management Protocol)
		- IGMP is a communication protocol used by hosts and adjacent routers for multicasting communication with IP networks and uses the resources efficiently to transmit messages/data packets.
		- Multicasting is implemented using special multicast routers that are able to route multicast packets
		- It is a protocol that manages Group membership
		- IGMP gives multicast routers information about membership status of hosts(routers) connected to the network.
			- A multicast router will receive thousands of multicast packets every day for different groups.
			- If a router has no knowledge about the membership status of the hosts, then it must broadcast all these packets.
			- This creates a lot of traffic and consumes bandwidth.
			- Solution: We maintain a list of the groups in the network for which there is at least one loyal member.
			- IGMP helps the multicast router create and update this list.
		- IGMP is used in IPv4 networks. Two kinds of packets are:
			- Query
			- Response
		- Multicast routing is done using Spanning Trees
	-