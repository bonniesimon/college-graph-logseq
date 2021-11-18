- Syllabus
	- Evolution of Distributed Computing -
	- Issues in designing a distributed system- Challenges-
	- Minicomputer model – Workstation model
	- Workstation-Server model– Processor - pool model
	- Trends in distributed systems
- ![Module 1 (ktuassist.in).pdf](../assets/Module_1_(ktuassist.in)_1637132826094_0.pdf)
- Distributed system consists of a collection of autonomous computers linked by a computer network and equipped with a distributed system software.
	- This software is used to coordinate activities and share resources.
- ## Evolution of Distributed Computing Systems
	- ??
## Challenges and Issues in Design of distributed systems
	- Heterogeneity
		- Internet enables users to access services and run applications over heterogeneous collection of computers and networks
		- Different programming languages use different representations for characters and DSs.
		- Programs developed by different programmers cannot communicate with one other unless they use common standards.
		- Middleware
			- Software layer that provides a programming abstraction as well as masking the heterogeneity of the underlying technologies.
			- Most middleware is implemented over internet protocols which masks the underlying network
				- but have to deal with the differences in OS and hardware.
		- Mobile code
			- Code that is written on one computer but transferred to another and executed at the destination
			- But not all code is suitable for all computers
				- we can solve this by using virtual machines
	- Transparency
		- Transparency is defined as hiding the nuances of the systems from the user. The system is to be perceived as a whole by the user
		- Complexity of the system must be hidden from the user
		- Terms in transparency
			- Access : hide differences in data representation
			- Location : hide where resources are located
			- Migration: Hide that a resource may move to another location
			- Relocation: Hide that a resource may move while in use
			- Replication: Hide that the resource may be copied in several places
			- Concurrency: Hide that the resource may be shared among users
			- Failure: Hide the failure and recovery of the resource
			- Persistence: Hide whether a resource is in disk or memory
	- Openness
		- Characteristic that determines whether the system can be extended or re-implemented in various ways
		- Degree to which a new resource sharing service can be added and made available for use for client programs
		- Designers must hide the complexity of the system as much as possible
		- Open systems are characterized by the fact that their key interfaces are published.
	- Security
		- Many of the resources made available and maintained in the distributed systems are of high intrinsic value to their users
		- So security is of considerable importance
		- Security consists of 3 components
			- Confidentiality
			- Integrity
			- Availability
	- Scalability
		- Distributed systems must be effective and efficient at different scales
			- ranging from small intranet to the internet
		- System is scalable if it can function effectively and efficiently even when there is a significant increase in number of users or resources
		- Challenges
			- controlling the cost of physical resources
			- controlling the performance loss
			- preventing software resources from running out
	- Failure Handling
		-