##### LS171 Assessment: Networking Foundations

---

## Key Ideas and Concepts

#### What is the Internet and how does it work?

The Internet may be conceived of a vast network of networks. At the most basic level, this means a vast interconnected system of computers, switches, and routers communicating with each other. The physical channels of communication include wires and radio waves. The Internet is designed in such a way that it is fully distributed with no central control deciding how information is routed or where pieces of the network are built, or even who interconnects those various pieces.

Like any system of communication, the Internet employs rules for how communication should occur over the network. Machines need to be able to speak the same language in order for orderly communication to take place. A protocol is the name for a set of rules used for network communication. The Internet employs different protocols for different aspects of network communication or for different purposes within the same aspect of network communication. Some protocols are concerned with the flow and order of messages (e.g. TCP), whereas other protocols are concerned with the structure of those messages (HTTP).

Thus, the Internet can be thought of a vast network of networks over which orderly communication between devices takes place in accordance with a set of protocols.

There are two main models that have been constructed in order to help us understand at a much deeper level what is going on "under the hood" of the Internet. Those two models are the Open Systems Interconnection (OSI) model and the Internet Protocol Suite model (also known as the TCP/IP model or DoD model). Both models break network communication down into separate layers (7 in the OSI model and 4 in the TCP/IP model):

OSI Model Layers (from the topmost layer):

* Application
* Presentation
* Session
* Transport
* Network
* Data Link
* Physical

TCP/IP Model Layers (from the topmost layer):

* Application
* Transport
* Internet
* Link

The top three layers of the OSI Model mostly map to the topmost layer of the TCP/IP Model. The Transport layer of both models are roughly equivalent, as are the Network and Internet layers of the respective models. The Datalink and Physical layers of the OSI model mostly map to the Link layer of the TCP/IP model.

Separating network communication into these separate layers allows us to group the various protocols according to which layer of communication with which they apply. The idea is that at each layer, protocols determine how the data that is moving across the network must be structured. At each layer, data is encapsulated within a data unit according to the rules defined by a specific protocol, and consequently hiding the data from the layer below it.

These data units are called protocol data units (PDUs), although these PDUs are given more specific names at different layers. For example, at the Transport layer, PDUs are called segments (TCP) or datagrams (UDP); at the Internet/Network layers they are called packets; and at the Link/Data Link layers they are called frames. But no matter what layer we are at, every PDU consists of a header, a data payload, and in some cases a trailer or footer.

The exact structure of the header and, if included, trailer depends on the specific protocol being used, but the purpose in each case is the same: to provide protocol-specific metadata about the PDU. 

The data payload portion of the PDU is just the data we want to transport over the network using a specific protocol at a particular network layer.  It is the key to the way that encapsulation is implemented: the data payload at one layer is simply the entire PDU from the layer above it. Thus, the PDU at one layer is encapsulated within the data payload of the PDU from the layer below. The layer below is essentially providding a service to the layer above it.

#### What are the characteristics of the physical network, such as latency and bandwidth?

It's easy to think of the Internet as something immaterial. It allows us to send messages without having to actually write something down on a physical piece of paper. But the Internet, at its most basic level, is a 'physical' network comprised of tangible pieces such as networked devices, cables, and wires. Even the radio waves used in wireless networks, though we can't touch or see them, exist in the physical realm and are bound by the physical laws and rules.

If we think of the Physical Layer of the OSI model, we are essentially concerned with the transfer of bits (binary data). In order to be transported, these bits are converted into signals. Depending on the transportation medium used, bits are converted to electrical signals, light signals, or radio waves. Because the Internet is comprised of physical devices and connections it faces physical constraints.

Two characteristics that concern those Internet's physical contstraints include latency and bandwidth. Latency refers to the _length of time_ it takes for some data to get from one point of the network to another point in a network, while bandwidth refer to the _amount of data_ that can be sent at once.

Latency is a measure of delay and there are four different types of delay that comprise the overall latency of any network connection: propagation delay, transmission delay, processing delay, and queuing delay. Propagation delay is the time it takes data to travel the distance between sender and receiver. Transmission delay is the time it takes data to traverse a network link. Processing delay is the time it takes data to be processed when it arrives at a link, or node, in the network. Queuing delay is the time it takes data to queue, or buffer, while it waits to be processed. The total latency between two points, such as a client and a server, is the sum of all of the delays above, usually measured in milliseconds (ms).

Last-mile latency is a concept that refers to the end part of the data's journey. There are usually more delays that take place near the end points of networks and thus it takes longer for data to traverse individual subnetworks than it does for it to traverse the core network. The 'hops' within the core part of the network are longer with less interruptions for transmission, processing, and queuing. At the network edge, there are more frequent and shorter hops as the data is directed down the network hierarchy to the appropriate sub-network. You can think of the network edge as the 'entry point' into a network like a home or corporate LAN.

Bandwidth, as mentioned, refers to the amount of data that can be sent at any one time. This amount is not a constant but will vary at different points throughout the network. For example, the capacity, or bandwidth, of the core network is going to be much higher than the part of the network infrastructure that ultimately connects to your home or office building. The bandwidth that a connection receives is the lowest amount at a particular point in the overall connection. A point at which bandwidth changed from relatively high to relatively low is generally referred to as a bandwidth bottleneck.

#### How do lower level protocols, such as Ethernet and IP, operate?

Just above the Physical Layer in the OSI model is the Data Link Layer. The TCP/IP model essentially wraps both of these layers into one Link Layer. The protocols operating at this layer are primarily concerned with the identification of devices on the physical network and moving data over the physical network between the devices that comprise it, such as hosts (e.g. computers), switches, and routers. This layer can be thought of as an interface between the workings of the physical network and the more logical layers above.

The most commonly used protocol at this layer is the Ethernet protocol and its two most important aspects are framing and addressing.

The PDU of the Ethernet protocol is known as a frame. It encapsulates data from the Internet/Network layer above. It is important to note that the Link/Data Link Layer is the lowest layer at which encapsulation takes place. At the physical layer, the data is essentially a stream of bits in one form or another without any logical structure. An Ethernet Frame adds logical structure to this binary data. The frame structures the data by defining which bits are the data payload and which bits are the metadata used in the process of transporting the frame.

That metadata includes a header, which includes the source and destination MAC addresses of the frame. A unique MAC address is assigned to each network-enabled device when it is manufactured (it is sometimes known as the physical address or burned-in address because it is permanent and does not change). The source address included in the header is the address of the device that created the frame (and this can change at various points along the data's journey). The destination MAC address is the address of the device for which the data is intended.

Local networks nowadays use switches to direct frames to the intended device. A switch does this by keeping and updating a record of the MAC addresses of the devices connected to it, and associating each address with the Ethernet port to which the device is connected on the switch. It keeps this data in a MAC Address Table, a simple representation of which might look something like this:

| Switch Port | MAC Address       |
| :---------- | :---------------- |
| 1           | 00:40:96:9d:68:0a |
| 2           | 00:A0:C9:14:C8:29 |
| 3           | D8:D3:85:EB:12:E3 |
| 4           | 00:1B:44:11:3A:B7 |

The MAC Addressing system works well for local networks, where all the devices are connected to a switch that can keep a record of each device's address. In theory, we could conduct inter-network communication just using MAC addresses. In practice, however, there's an issue that prevents us from doing this: scale. This approach isn't scalable because: 1) MAC addresses are physical rather than logical in that each MAC Address is tied to a specific physical device; and 2) MAC Addresses are flat rather than hierarchical, meaning the entire address is a single sequence of values and can't be broken down into sub-divisions.

This problem is solved at the next layer above, the Network/Internet Layer.  