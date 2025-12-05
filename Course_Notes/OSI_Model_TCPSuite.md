# 3. OSI MODEL & TCP/IP SUITE

## What is a networking model?

Networking models categorize and provide a structure for networking protocols and standards.

(Protocols are a set of logical rules defining how network devices and software should work)

## OSI MODEL

- Open Systems Interconnection Model
- Conceptual model that categorizes and standardizes the different functions in a network.
- Created by the "International Organization for Standardization" (ISO)
- Functions are divided into 7 "Layers"
- These layers work together to make the network work.

![image](https://github.com/psaumur/CCNA/assets/106411237/bbf46de2-e025-4ddd-b52b-614b280598da)

As data moves from the top layer, downward, the process is called “encapsulation”

As data moves from the bottom layer, upward, the process is called “de-encapsulation”

When interactions occur on the same layer, it’s called “same-layer interaction”

![image](https://github.com/psaumur/CCNA/assets/106411237/b7cf4900-993c-49f0-b6ea-70f4f0719633)

Mnemonic to help remember the Data Layer Names / Order

![image](https://github.com/psaumur/CCNA/assets/106411237/01f532f6-b636-4b7c-99d0-a67f7e483a99)


### The layers are :

### 7 - APPLICATION

- This Layer is closest to end user.
- Interacts with software applications.
- HTTP and HTTPS are Layer 7 protocols

Functions of Layer 7 include:

- Identifying communication partners
- Synchronizing communication

---

### 6 - PRESENTATION

- Translates data to the appropriate format (between Application and Network formats) to be sent over the network.

---

### 5 - SESSION

- Controls dialogues (sessions) between communicating hosts.
- Establishes, manages, and terminates connections between local application and the remote application.

---

Network engineers don't usually work with the top 3 layers.
Application developers work with the top layers of the OSI model to connect their applications over networks.

---

### 4 - TRANSPORT

- Segments and reassembles data for communication between end hosts.
- Breaks large pieces of data into smaller segments which can be more easily sent over the network and are less likely to cause transmission problems if errors occur.
- Provides HOST-TO-HOST (end to end) communication

When Data from Layer 7-5 arrives, it receives a Layer 4 Header in the Transport layer.

<< DATA + L4 Header >>

This is called a SEGMENT.

---

### 3 - NETWORK

- Provides connectivity between end hosts on different networks (ie: outside of the LAN).
- Provides logical addressing (IP Addresses).
- Provides path selection between source and destination
- **ROUTERS** operate at Layer 3.

When Data and the Layer 4 Header arrive in the Network Layer, it receives a Layer 3 Header.

<< DATA + L4 Header + L3 Header >>

This is called a **PACKET**.

---

### 2 - DATA LINK

- Provides NODE-TO-NODE connectivity and data transfer (for example, PC to Switch, Switch to Router, Router to Router)
- Defines how data is formatted for transmission over physical medium (for example, copper UTP cables)
- Detects and (possibly) corrects Physical (Layer 1) errors.
- Uses Layer 2 addressing, separate from Layer 3 addressing.
- **SWITCHES** operate at Layer 2

When the Layer 3 Packet arrives, a Layer 2 Trailer and Header are added.

<< L2 Trailer + DATA + L4 Header + L3 Header + L2 Header >>

This is called a FRAME.

All the steps leading up to transmission is called ENCAPSULATION.
When the frame is sent to the receiver, it then goes through the reverse process, DE-ENCAPSULATION, stripping off layers while travelling from OSI Layer 1 to Layer 7.

---

### 1 - PHYSICAL

- Defines physical characteristics of the medium used to transfer data between devices. For example : voltage levels, maximum transmission distances, physical connectors, cable specs.
- Digital bits are converted into electrical (for wired connections) or radio (for wireless connections) signals.
- All of the information in SECTION 2 (NETWORKING DEVICES) is related to the Physical Layer

---

### OSI MODEL - PDU's

![image](https://github.com/psaumur/CCNA/assets/106411237/9b885a51-91cd-4fe6-b1be-e7fa7aa220b5)

A PDU is a Protocol Data Unit. Each step of the process is a PDU.

| OSI LAYER # | PDU NAME | PROTOCOL DATA ADDED |
| --- | --- | --- |
| 7-5 | DATA | Data |
| 4 | SEGMENT | Layer 4 Header Added |
| 3 | PACKET | Layer 3 Header Added |
| 2 | FRAME | Layer 2 Trailer and Header Added |
| 1 | BIT | 0s and 1s Transmission |

<< L2 Trailer + DATA + L4 Header + L3 Header + L2 Header >>

---

### TCP/IP Suite

- Conceptual model and set of communications protocols used in the Internet and other networks.
- Known as TCP/IP because those are two of the foundational protocols in the suite.
- Developed by the US Dept. of Defense through DARPA (Defense Advanced Research Projects Agency).
- Similar structure to the OSI Model, but fewer layers.
- THIS is the model actually in use in modern networks.
- * Note : The OSI Model still influences how network engineers think and talk about networks.

![image](https://github.com/psaumur/CCNA/assets/106411237/e9593c06-46a3-4ff9-aa01-863e0aeb5df3)

### TCP/IP MODEL

![image](https://github.com/user-attachments/assets/f8af214a-8c3f-4a03-8c15-22f25649922e)

#### Layer 1 (Physical Layer)

Starting at the bottom of the TCP/IP model we're using, the **Physical Layer** sends and receives bits as electrical, optical or radio signals over the medium. \
It defines cables, connectors, signal levels and link speeds. \
Examples are copper UTP cables, fiber-optic cables, WiFi- radios and antennas, NICs.

Each network interface has a NIC like this inside of the device and the physical aspects of transmitting data are very complex.

Note that in some 4-layer TCP/IP models this layer and the next layer are combined but it may be useful to differentiate the physical concerns like these and the logical aspects of Layer 2.

#### Layer 2 (Local Network Layer)

The **Local Network Layer** provides hop-to-hop delivery of messages on a LAN. \
A hop is one step along the path that the message travels over the network to the device you're trying to reach. 
This step is from a router or host to the next router or host in the path.
  
Important to note is that switches *do not* count as hops, a switch extends the local network, allowing multiple devices to connect. 
- Uses MAC (Mesource dia Access Control) addresses to identify each interface. \
Each device (connected to a LAN) has a specific MAC-address for that specific interface.

##### Protocols on Layer 2

- Ethernet (IEEE 802.3)
- Wi-Fi (IEEE 802.11)
Other protocols exist on this Layer but these are most important for the CCNA because they are by far the most commonly used protocols on this Layer.

#### Layer 3 (Internet Layer)

- Provides end-to-end delivery between hosts across multiple networks, meaning it focuses on getting the message from the source host all the way to the final destination host. \
  It won't worry about each indiviudual hop in between.
- Internet = internetwork (between networks).
- Identifies hosts in the network using IP addresses.
- Routers operate mainly at this layer, using the message's destination IP adress to forward each message to its final destination host.

##### Protocols on Layer 3

- IP (IPv4, IPv6)
- ICMP (Internet Control Message Protocol

#### Layer 4 (Transport Layer)

- Provides end-to-end communication between application processes, for example from your browser to the web server.
- Servers can provide multiple services, to know which service you require it uses **port numbers** to identify processes.
- Routers normally operate based on Layer 3 and Layer 4 mainly operates on the communicating hosts such as a PC or server.

##### Protocols on Layer 4

- UDP (User Datagram Protocol): simple and efficient
- TCP (Transmission Control Protocol): more robust features beyond basic message addressing

#### Layer 5 (Application Layer)

- Layer 5 is where network communications meet applications.
- Usually called Layer 7 (OSI Model).
- Defines how application processes format, send and interpret data.
- Networking devies such as a router typically don't care about Application Layer details. \
  Only the communicating hosts interpret the data.

##### Protocols on Layer 5

- Browsing web pages (HTTP & HTTPS)
- Transferring files (FTP & TFTP)
- Email (SMTP, POP3, IMAP)

---

#### Encapsulation / Decapsulation

##### Encapsulation

When a PC has a message for a server this is the process covering each layer:
- The **Application Layer** prepares the data to be sent over the network.
- As the message moves down the stack, each layer **encapsulates** the data with a **header** containing the information needed by that layer.
  Think of source destination addresses (port numbers, IP addresses, MAC-addresses), etc.

- The **Transport Layer** encapsulates the data with a L4 (Layer 4) header.
- The **Internet Layer** add its header with source and destination addresses.
- Layer 2 adds a header and also a **trailer** that the receiving device uses to check for transmission errors.

- Next, the **Physical Layer** transmits the bits as signals over the physical medium.
- The L2 header is transmitted first, and the L2 trailer is transmitted last.

![image](https://github.com/user-attachments/assets/1d4e6156-abed-44a2-bc66-6517cb09fffd)

---

##### Decapsulation

- Receiving devices receives the message as a stream of bits at Layer 1.
- The information in the L2 header & trailer gets examined and then gets removed (either called decapsulation or deencapsulation).

The decapsulation process continues up the stack:
- L3 removes the L3 header.
- L4 removes the L4 header.
- Then the data is delivered to the Application Layer.
- The application processes the data and, if needed, generates a response that goes back down the stack.

Each device has its own network stack. \ 
A message from a source host goes down the stack, goes over the physical medium and then crosses the stack on the other host.

---

##### Protocol data units

- At each stage in the encapsulation/decapsulation process, there is a name given to the message.
- Data + a L4 header is either called a **segment** (TCP) or **datagram** (UDP) (L4PPDU) \
  This has to do with how these 2 protocols treat the data.
- Segment/datagram + a L3 header is called a **packet**. (L3PDU) \
  A **packet** is the most common term used when talking about message being sent over a network.
- Packet + L2 header/trailer is a **frame**. (L2PDU) \
  This is what is sent over the physical medium.

The contents of each PDU meaning everything encapsulated by that specific layer's header/trailer are called the **payload**.
- A segment or datagram's payload is the application data.
- A packet's payload is a segment or datagram.
- A frame's payload is a packet.

---

### Layer Interactions

![image](https://github.com/psaumur/CCNA/assets/106411237/372c45a0-bb3e-4342-af2b-79d3606384ec)

These layer interactions apply for both the TCP/IP model and the OSI model, psaumur used the OSI model.

Adjacent-Layer Interactions:

- Interactions between different layers of the OSI Model on same host.

Example (OSI):

Layers 5-7 sending Data to Layer 4, which then adds a Layer 4 header (creating a SEGMENT). 

Same-Layer Interactions:

- Interactions between the same Layer on different hosts.
- The concept of Same-Layer interaction allows you to ignore the other layers involved and focus on the interactions between a single layer on different devices.

Example:

The Application Layer of YouTube's web server and your PC's browser.

---

As long as each layer keeps its "contract" you can use improve or replace protocols on each individual layer without redesigining everything.

--- 

### Review
It is recommended to review the following to make sure you understand it. \
Perhaps use Jeremy's flashcards.

- TCP/IP Model Layers – purpose of each layer (Application, Transport, Internet, Link).
- OSI‑derived Names – common alternate names for the TCP/IP layers (e.g., “Network” for Internet, “Data Link” for Link).
- Encapsulation / Decapsulation – how headers (and trailers) are added at the sender and stripped at the receiver.
- Protocol Data Units (PDUs) –
- Layer 4: Segment (TCP) / Datagram (UDP)
- Layer 3: Packet
- Layer 2: Frame (the unit placed on the physical medium)
- Adjacent‑Layer Interaction – how each layer talks to the layer directly above and below it within the same host.
- Same‑Layer Interaction – how a layer on one device communicates with its counterpart on another device (e.g., Transport‑to‑Transport, Network‑to‑Network).
