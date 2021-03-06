# Week 2
- ## 6LoWPAN
	- Low power Wireless Personal Area Network over IPv6
	- Allows for the smallest devices with limited processing ability to transmit information wirelessly using internet protocol.
	- Allows low power devices to connect to the internet.
- ## RFID
	- Radio Frequency Identification
	- Data digitally encoded in RFID tags, which can be read by a reader.
	- Somewhat similar to bar codes.
	- Compared to barcodes, data in RFID tag can be read without line of sight
	- Working principle
		- RFID uses radio waves to perform AIDC functions
		- AIDC is Automation Identification and Data Capture technology.
		- RFID derived from AIDC.
		- AIDC uses wired communication
	- Applications
		- Inventory management
		- Asset tracking
		- personnel tracking
		- ID badging
- ## MQTT
	- Message Queue Telemetry Transport
	- lightweight messaging protocol
	- publish subscriber based
	- used in conjunction with TCP/IP protocol
	- A topic to which a client is subscribed is updated in the form of messages by the message broker.
	- MQTT components
		- Publishers
		- Subscribers
		- Brokers
			- connect subscribers and publishers
	- Architecture
		- MQTT uses publisher-subscriber architecture. HTTP uses request-response architecture.
		- Publisher subscriber is event driven
	- Applications
		- FB messenger uses MQTT for online chat
		- Amazon Web services uses MQTT with amazon IoT
- ## CoAP
	- Constrained Application Protocol
	- Web transfer protocol for constrained nodes and networks.
	- Designed for M2M applications.
	- Based on Request Response model
	- It is a session layer protocol
	- CoAP enables low power sensors to use RESTful services while meeting their power constraints.
	- Built over UDP instead of TCP
- ## XMPP
	- Extensible Messaging and Presence Protocol
	- A communication protocol for message oriented middlewares based on XML
	- Real time exchange of structured data
	- uses client server protocol
	- Decentralized; i.e no central server is required. Anyone can run their XMPP server.
	- Data must be first encoded to base64 before tansmission
## AMQP
	- Advanced Message Queuing Protocol
	- Open standard for passing business messages between application or organizations
	- it is a binary application layer protocol.
	- Basic unit of data is a frame.
	- High speed protocol
	- AMQP frame types
		- Open - connection open
		- Begin - session open
		- attach - initiate new link
		- Transfer - for sending actual messages
		- Flow - controls message flow rate
		- Disposition - informs the changes in state of transfer
		- Detach - terminate the link
		- End - session close
		- Close - connection close
- (skipped the next part IEEE 802.15.4)
# Week 3
## HART & Wireless HART
	- Highway Addressable Remote Transducer (HART) Protocol
	- Wireless protocol makes HART cheaper and easier.
	- Wired HART lacks a network layer.
	- HART Physical Layer
		- Operates only in the 2.4GHz ISM band.
	- HART Data link layer
		- Collision free and deterministic communication achieved by means of super frames and TDMA
		- This layer incorporates channel hopping and channel blacklisting to increase reliability and security.
	- HART Network & Transport Layer
		- Cooperatively handle various types of traffic, routing, session creation and security.
		- WirelessHART relies on Mesh Networking for its communication,
			- and each device is primed to forward packets from every other devices.
		- Each device is armed with an updated network graph to handle routing
		- Network Layer (HART) = Network + Transport + Session Layers (OSI)
	- HART Application Layer
		- Handles communication between gateways and devices
			- via a series of command and response messages.
			- This layer is seamless and does not differentiate between wireless and wired versions of HART
	- HART Congestion Control
		- Transmission synchronized using 10ms slots
	- WirelessHART represents a true mesh network
	- WirelessHART devices are all back compatible.
	- WirelessHART network manager handles code-based network security
## NFC
	- Near Field Communication
	- It is an offshoot of RFID
	- NFC is designed for use by devices within close proximity to each other.
	- NFC Types
		- Passive devices
			- Can contain information
			- can't read information
		- Active devices
			- Can collect and transmit information
	- Working Principle
		- Works on the principle of Magnetic Induction
	- NFC modes of operation
		- Peer to peer
		- Read/write
		- Card emulation
	- Does not use standard 2.4GHz ISM band
		- while ZigBee, Bluetooth and 6LoPAN uses 2.4GHz ISM band
## Bluetooth
	- is a short range wireless communication technology
	- Maintains high levels of security
	- based on ad hoc technology know as adhoc piconets
	- operates in the ISM band at 2.4 to 2.485GHz
	- uses spread spectrum hopping,
	- Connection establishment
		- Inquiry
			- inquiry run by one Bluetooth device to try to discover other devices near it.
		- Paging
			- process of forming a connection between two bluetooth devices
		- Connection
			- Device either actively participates or enters sleep
	- Baseband
		- Physical layer of the bluetooth
		- manages physical channels and links
		- error correction, hop selection, bluetooth security
		- handles packets, paging and inquiry
	- L2CAP
		- Logical link control and adaptation protocol
		- resides in the data link layer
	- There are power three saving modes in blutooth
	- (some more parts of bluetooth remaining that I haven't studied)
## Z Wave
	- protocol for communication among devices used for home automation
	- uses RF for signaling and control
	- mesh network topology is the main mode of operation
	- utilizes GFSK modulation and Manchester channel encoding
## ISA 100.11A
	- International Society of Automation
	- Designed mainly for large scale industrial complexes and plants
	- Network and transport layer are based on TCP or UDP over IPv6
	- Data link layer supports mesh routing and frequency hopping
	- Security is fully built in to the standard
	- Authentication and confidentiality services are independently available.
	- For control applications class 0, class1, and class 2 are used.
## Sensor Nodes
	- Constraints on sensor nodes
		- small size
		- consume low power
		- low production cost
		- be dispensable
		- autonomous
		- adaptive to the environment
# Week 4
## WSN
	- Each of the board is enabled with two types of sensors
		- Passive Infrared
			- Used to detect objects
				- sense motion of objects
				- detect emitted infrared energy from objects
		- Ultrasonic
## Optimal Geographical Density Control (OGDC) Algorithm
	- It comes under the Distributed and Localized area coverage algorithm
	- Starting node broadcasts a message containing **ideal direction**
## Coverage
	- Barrier Coverage
		- K-barrier coverage ensures that a particular barrier is covered by al least k sensors.
## UAV
	- Star topology is not self configuring
	- Mesh topology is self configuring
	- UAV network constraints
		- Frequent link breakages
		- Prone to malfunction
		- huge power requirements
		- very complex
		- physically prone to environmental effects
## FANETS
	- Flying Ad Hoc Networks
## Machine to Machine communication
	- Similar to SCADA (Supervisory control and data acquisition)
	- M2M Application platform
		- seamless service and connection management
# Week 5
## Interoperability
	- 6LowPAN and IEEE802.15.4 (bluetooth) allow interoperability
	- EPC is used to generate unique address
		- UPC and URI and IP addresses as well
	- Different device classification solution
		- UNSPSC
			- United nations Standard Products and Services Code
			- an open, global, multi-sector standard for efficient, accurate, flexible classification of products and services
		- ECI@ss
			- The standard is for classification and clear description of cross inductry products
	- Syntactic interoperability for device interaction
		- popular approaches
			- SOC
			- Web services
			- RESTful web services
			- 802.25.4, 802.15.1, WirelessHART
			- Z-wave
	- Semantic Interoperability for device interaction
		- popular approaches
			- Device ontology
			- physical domain ontology
			- estimation ontology
	- Universal Middleware Bridge (UMB)
		- Event handler UMB architecture sends and receives the events generated by changing the device's status
		- UMB adaptor
			- converts physical devices into virtually abstracted one
			- translate the local middleware's message into global metadata's message
		- UMB core
			- routing the universal metadata message to the destination or any other UMB adaptor
## Intro to Arduino Programming
	- Open source based electronic programming board (micro controller) and software (IDE)
	- Accepts analog and digital signals as input and gives desired output
	- Based on variations of the C and C++ programming language
	- Arduino Uno uses ATMEGA328p
	- Sketch is divide into two parts
		- Setup()
			- It is the point where the code starts kinda like main() in c
			- I/O variables, pin modes are initialized in the setup() function
		- Loop()
			- Iterates the specified task in the program
	- delayMicroseconds() returns Unsigned int
	- SERVO
		- Arduino provides a library to operate the servo motors
		- Some functions available in the servo library
			- Knob()
			- sweep
			- write
			- writeMicroseconds
			- read
			- attached
			- detach
# Week 6
- Raspberry Pi 3 has on-board bluetooth module
- time.sleep(arg) takes in seconds as argument
- There are 40 GPIO (General Purpose Input Output) pins in Raspberry Pi 0
- ord() used to convert characters to intergers.
- from picamera import PiCamera is the right way to import the operations on the on-board camera in Raspberry Pi
# Week 7
## Software Defined Networks
	- The switches in SDN have global view of the network
	- Switches are controlled using a centralized manner.
	- Traditional network uses routing table
		- Software defined networks use flow table
	- Components of a switch
		- Application
		- Operating system
		- Specialized hardware
	- Controller placement architectures
		- Flat
		- Ring
		- Tree
	- SDN architecture has 3 layer/planes
	- Communication between layer/planes in a SDN is done using API's
# Week 8
- In comparison to SDN, traditional networks are cost expensive with respect to both capital expenditure and operational expenditure
- Logically Centralized Control is useful for efficient base station coordination for addressing inter cell interference
- Flow scheduling in ubiflow perform
	- Network partition
	- Network matching
	- Load balancing
- In Mobi-Flow the proactive rule placement depends on the user movement
- Mobi-Flow reduces both energy consumption and message overhead
- To detect anomalies in a network, you should monitor the network flow
## Cloud Computing
	- NIST Visual Model of Cloud Computing
		- Essential Characteristics / Cloud characteristics
			- Broad Network Access
			- Rapid elasticity
			- Measured services
			- On-demand self-services
			- Resource pooling
		- Service models
			- Software as a service
				- A third party provides a host application over internet
				- Eg : Microsoft office 365
			- Platform as a service
				- Provides a platform to develop and run applications
				- Eg: Microsoft Azure
			- Infrastructure as a service
				- Provide computing resources
				- Eg: Storage space
		- Deployment models
			- Public
			- Private
			- hybrid
			- Community
	- Sharing of cloud resources and cost across a large pool of users is called Multitenancy
	- Thin clients require constant communication/connection with the cloud server
	- Although cloud computing users should feel that they have infinite supply of resources, its utilization should be constantly monitored.
	- Cloud computing has 6 components
		- Clinets
		- services
		- application
		- platform
		- storage
		- infrastructure
# Week 9
## Wireless Sensor Networks (WSN)
	- Contain sensor nodes which sense some physical phenomena from the environment
	- Transmit the sensed data (through wireless communication) to a centralized unit, called Sink node.
	- Communication between sink node and other sensor nodes may be single or multiple hop
	- Sink node further process the data.
	- Components of sensor node
		- Sensing unit
		- Processing unit
		- Communication unit
	-
## Virtualization Concept
	- Concept of VM - One computer host appears as many computers
## Sensor Cloud
	- Actors in Sensor cloud
		- End users
		- Sensor owner
		- Sensor Cloud Service Provider
			- Charge price from the end users as per their usage of Se-aaS
			- Responsible for caching the data in the databases
	- In sensor cloud workflow, the virtual sensor manager sends to the resource manager the release resource message
## Fog Computing
	- The idea of fog computing is to extend the cloud nearer to the IoT devices
	- An intermediate layer between cloud and devices
	- Issues with cloud computing
		- Volume
		- Latency
		- Bandwidth
	- Fog provides transient storage
# Week 10
## Smart City
	- Analogy
		-
		  |Humans | Smart Cities|
		  |------|------|
		  | Skeleton | Buildings, Industries, people |
		  |Skin| Transportation, Logistics|
		  |Organs|Hospital Police Banks, schools|
		  |Brain|Ubiquitously embedded intelligence|
		  |Nerves|Digital Telecommunication networks|
		  |Sensory organs|Sensors, Tags|
		  |Cognition|Software|
	- Need for smart city
		- Rapidly growing urban populations
		- Fast depleting natural resources
		- Changes in environment and climate
	- Application of Focus areas
		- Smart Economy - Competitiveness
		- Smart governance - citizen participation
		- Smart people - social and human capital
		- Smart mobility - transport and ICT
		- smart environment - natural resources
		- smart living - quality of life
	- Smart homes should focus on
		- health monitoring
		- conservation of resources (eg. electricity, water, fuel)
		- security and safety
	- Smart vehicles should focus on
		- assitance to drivers during bad weather or low visibility
		- detection of bad driving patterns or driving under the influence of substances
		- auto alert generation during crashes
		- self diagnostics
	- Both traditional and renewable energy sources may be placed on the same smart grid
	- IOT challenges in smart cities
		- Security and Privacy
			- Multi-tenancy may induce the possibility of data leakage
		- Heterogeneity
			- Integration of varying hardware platforms and specifications
			- Integration of different radio specifications
			- Integration of various software platforms
			- Accommodating varying user requirements
		- Reliability
		- Large scale
			- Delay due to large scale deployments
			- Delay due to mobility of deployed nodes
			- Distribution of devices can affect monitoring tasks
		- Legal and social aspects
		- Big data
	- Both individual and informed consent must be required to use humans as data sources
	- Device placement and network architecture is important for reliable end to end IoT implementation
	- Security
	- Mobility is a main challenge in connected vehicles in comparison to that of smart cities
	- V2X - Vehicle to Everything
# Week 11
## Smart Grid
	- Smart Grids enable bidirectional flow of energy, bidirectional communication and an array of founctionalities and applications
	- Power restoration time in traditional grids after disturbances is higher
	- Running smart devices during peak hours results in higher energy bills
	- Both consumers and stakeholders are benefited on using smart grids
	- Micro grids can detach from main smart grids at any point of time without disrupting the core grid
	- Consumer participation is the property of smart grids that is responsible for controlling appliances
	- Property of maintaining power quality in smart grids facilitate Load Forecasting
	- Computerized control helps in minimizing energy use in smart homes when the power grid is under stress.
	- Smart meters provides the smart grids an interface between the consumers and the energy service providers
## IIOT (Industrial Internet of Things)
	- Internet of things INTERSECTION Industry 4.0 = IIoT
	- IoT deals with consumer IoT
	- IIOT deals with Enterprise IoT
	- IIOT is based on the "wrap & re-use" approach
	- Order of occurence
		- Mechanized production
		- Mass production
		- Internet evolution and automation
		- IIoT
## Big Data
	- Big data is characterized by 7 Vs
		- Volume
			- Quantity of data
		- Velocity
			- Speed of generation of data
		- Variety
			- category to which the data belongs to
		- Variability
			- Data whose meaning is constantly changing
		- Veracity
			- refers to biases, noise and abnormality in data
		- Visualization
			- Presentation of data in a pictorial or graphical format
		- Value
			- Extracting useful business information from scattered data