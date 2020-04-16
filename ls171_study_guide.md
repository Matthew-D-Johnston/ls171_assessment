##### LS171 Assessment: Networking Foundations

---

# Study Guide

## The Internet

##### Have a broad understanding of what the internet is and how it works

* The internet is made up of an incredibly large number of independently operated networks.
* The internet is fully distributed: there's no central control that is deciding how packets are routed or where pieces of the network are built, or even who interconnects with whom. These are all business decisions that are made independently by the operators. They are all motivated to assure that there is end-to-end connectivity of every part of the network because the utility of the net is that any device can communicate with any other device; just like you want to be able to make phone calls to any other telephone in the world.
* Broadly, the internet is a network of networks.
* At its most basic, a network is comprised of at least two devices connected in such a way that they can communicate or exchange data.
* A Local Area Network (LAN) is essentially a network of computers all connected to a network bridging device, such as a hub or, more likely, a switch. The computers are all connected to this device via network cables and this forms the network.
* The internet can be imagined as a vast number of these networks connected together. In between all the sub-networks are systems of routers that direct the network traffic.

###### Protocols for Network Communication can be Organized Into a Layered Model

* Two of the most popuarl models are the Opens Systems Interconnection (OSI) model and the Internet Protocol Suite (also known as the TCP/IP or DoD model). There is some rough equivalency, albeit with some overlap, between the layers of the two models.
* The top layer of the Internet Protocol Suite (Application) mostly maps to the top three layers of the OSI Model (Application, Presentation, Session).
* The second layer of the Internet Protocol Suite (Transport) mostly maps to the fourth layer of the OSI model (Transport).
* The third layer of the Internet Protocol Suite (Internet) mostly maps to the fifth layer of the OSI model (Network).
* The fourth layer of the Internet Protocol Suite (Link) mostly maps to the bottom two layers of the OSI model (Data Link and Physical).

###### Protocol Data Units (PDUs)

* Each layer encapsulates data within a data unit of the layer below, thus hiding that data from other layers.
* Data is encapsulated into a PDU, creating separation between protocols operating at differnt layers.
* A PDU is an amount or block of data transferred over a network. Different protocols or protocol layers refer to PDUs by different names. At the Link/Data Link layer, for example, a PDU is known as a _frame_. At the Internent/Network layer it is known as a _packet_. At the Transport layer, it is known as a _segment_ (TCP) or _datagram_ (UDP).
* In all cases, the basic concept is effectively the same; the PDU consists of a header, a data payload, and in some cases a trailer or footer.
* Header and Trailer:
  * The exact structure of the header and, if included, trailer varies from protocol to protocol, but the purpose of them is the same in each case: to provide protocol-specific metadata about the PDU. For example, an Internet Protocol (IP) packet header would include fields for the Source IP Address and the Destination IP Address, which would be used to correctly route the packet.
* Data Payload:
  * The data payload portion of a PDU is simply the data that we want to transport over the network using a specific protocol at a particular network layer.
  * The data payload is the key to the way encapsulation is implemented. The entire PDU from a protocol at one layer is set as the data payload for a protocol at the layer below. For example, a HTTP Request at the Application layer could be set as the payload for a TCP segment at the transport layer.
  * The major benefit of this approach is the separation it creates between the protocols at different layers. This means that a protocol at one layer doesn't need to know anything about how a protocol at another layer is implemented in order for those protocols to interact. It creates a system whereby a lower layer effectively provides a 'service' to the layer above it. In other words, a TCP segment isn't really concerned whether its data payload is an HTTP request, an SMTP command, or some other sort of Application layer data. It just knows it needs to encapsulate _some data_ from the layer above and provide the result of this encapsulation to the layer below.

##### Understand the characteristics of the physical network, such as latency and bandwidth

* At the most basic level, or layer, we have a 'physical' network made of tangible pieces such as networked devices, cables, and wires. Even the radio waves used in wireless networks, though we can't touch or see them, exist in the physical realm and are bound by the physical laws and rules.
* These laws and rules determine how data actually gets transported from one placed to another in a physical sense. What happens at this level involves real-world limitations and boundaries, such as how fast an electrical signal or light can travel, or the distance a radio wave can reach. These limitations determine the physical characteristics of a network, and these characteristics have an impact on how protocols function further up at the conceptual level. 

###### Bits and Signals

* At the Physical Layer of the OSI model, we are essentially concerned with the transfer of bits (binary data). In order to be transported, these bits are converted into signals. Depending on the transportation medium used, bits are converted to electrical signals, light signals, or radio waves.

###### Characteristics of a Physical Network

* The two main characteristics of the performance of a physical network are Latency and Bandwidth.
* In simple terms, latency is a measure of the _time_ it takes for some data to get from one point in a network to another point in a network.
* Bandwidth is the _amount_ of data that can be sent at once.

###### The Elements of Latency

* Latency is a measure of delay. Data starts at one location at a certain point in time. At a later point in time, it reaches another location. The difference between those two points in time is the delay. There are actually different types of delay that go together to determine the overall latency of a network connection.
* **Propagation delay:** this is the amount of time it takes for a message to travel from the sender to the receiver, and can be calculated as the ratio between distance and speed.
* **Transmission delay:** the journey of data from point A to point B on a network typically won't be made over one single cable. Instead, the data will travel across many different wires and cables that are all inter-connected by switches, routers, and other network devices. Each of these elements within the network can be thought of as an individual 'link' within the overall system. Transmission delay is the amount of time it takes to push the data onto the link.
* **Processing delay:**  Data travelling across the physical network doesn't directly cross from one link to another, but is processed in various ways.
* **Queuing delay:** Network devices such as routers can only process a certain amount of data at one time. If there is more data than the device can handle, then it queues, or _buffers_, the data. The amount of time the data is waiting in the queue to be processed is the queuing delay.
* The total latency between two points, such as a client and a server, is the sum of all the delays above. This value is usually given in milliseconds (_ms_).
* **Last-mile latency**: a lot of the delays described above can take place within the parts of the network which are closest to the end points. This is often referred to as 'last-mile latency' and relates to the delays involved in getting the network signal from your ISP's network to your home or office network. The 'hops' within the core part of the network are longer with less interruptions for transmission, processing, and queuing. At the network edge, there are more frequent and shorter hops as the data is directed down the network hierarchy to the appropriate sub-network. You can think of the network edge as the 'entry point' into a network like a home or corporate LAN.

###### Bandwidth

* Bandwidth varies across the network, and isn't going to be at a constant level between the start point and the end point of our data's journey. For example, the capacity of the core network is going to be much higher than the part of the network infrastructure that ultimately connects to your home or office building. The bandwidth that a connection receives is the lowest amount at a particular point in the overall connection. A point at which bandwidth changes from relatively high to relatively low is generally referred to as a bandwidth bottleneck.

##### Have a basic understanding of how lower level protocols operate

* Protocols are systems of rules.
* In terms of computer networks, protocols are sets of rules governing the exchange or transmission of data.
* There are two main reasons for the existence of different protocols: 1) different protocols were developed to address different aspects of network communication; and 2) different protocols were developed to address the same aspect of network communication, but in a different way or for a specific use-case.

###### Different Protocols for Different Aspects of Communication

* syntactic rules that govern the structure of messages.
* Protocols at one layer provide services to the layer above.
* flow and order of the messages.
* In human communication we have grammatical rules governing speech and writing, we tend to follow certain conventions when speaking, such as allowing one person to speak at a time.
* TCP and HTTP would be examples of two protocols that address different aspects of communication; TCP the transfer of messages beetween applications, and HTTP the structure of those messages.

###### Different Protocols for the Same Aspect of Communication

* Certain specific contexts may require a different protocol.
* In human communication, we have different contexts with different protocols, such as a protocol for a conversation between two friends versus a protocol for a speaker at a conference. These contexts are still concerned with using proper syntax and following the flow and order of message transfer, but follow slightly different rules, or protocols.
* TCP and UDP would be examples of two protocls that address the same basic aspect of communication, the transfer of messages between applications, but do so in different ways. 

##### Know what an IP address is and what a port number is

* Point

##### Have an understanding of how DNS works

* Point

##### Understand the client-server model of web interactions, and the role of HTTP as a protocol within that model

* Point

---

## TCP & UDP

##### Have a clear understanding of the TCP and UDP protocols, their similarities and differences

* Point

##### Have a broad understanding fo the three-way handshake and its purpose

* Point

##### Have a broad understanding of flow control and congestion avoidance

* Point

---

## URLs

##### Be able to identify the components of a URL, including query strings

* Point

##### Be able to construct a valid URL

* Point

##### Have an understanding of what URL encoding is and when it might be used

* Point

---

## HTTP and the Request/Response Cycle

##### Be able to explain what HTTP requests and responses are, and identify the components of each

* Point

##### Be able to describe the HTTP request/response cycle

* Point

##### Be able to explain what status codes are, and provide examples of different status code types

* Point

##### Understand what is meant by 'state' in the context of the web, and be able to explain some techniques that are used to simulate state

* Point

---

## Security

##### Have an understanding of various security risks that can affect HTTP, and be able to outline measures that can be used to mitigate against these risks

* Point

##### Be aware of the different services that TLS can provide, and have a broad understanding of each of those services

* Point

