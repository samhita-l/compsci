---
toc: true
comments: false
layout: post
title: 4.1 - The Internet
description: Internet and basic protocols
type: tangibles
courses: { compsci: {week: 14} }
---

## 4.1 The Internet

# IP Address

What is an IP Address: A numeric label assigned to every device that uses the internet to communicate. IP stands for Internet Protocol. IP addresses are the identifiers that allow data to be sent over the internet. 
 - contain location information
 - allows devices to communicate over internet
 - differentiates between computers, routers, and websites

A set of 4 8-bit numbers seperated by periods. Each number is in the range 0-255. Exceptions are 0.0.0.0 and 255.255.255.255
 - 4.20.0.255
 - 16.23.234.1

![ipaddresstypes](https://cdn.discordapp.com/attachments/1174180230039081021/1178943626085142548/Screenshot_2023-11-27_220128.png?ex=6577fbd0&is=656586d0&hm=1aa0164e3e80e3c7fb6228ed7dc54291be578dea24db40b251e7df41835237c7&)

IP Addresses allow us to send information in three main ways.
1. Unicast - a specific device. Internet wide access. TCP is used
2. Multicast - a group of devices. It is specific range of IP addresses. Internet-wide access. UDP is used
3. Broadcast - all devices. LAN-wide. Data stops at the router. UDP is used

> Popcorn Hack - Finding your IP
 - https://www.whatsmyip.org/ works for both mac and windows
 - Alternatively, you can open up a command prompt (cmd into search bar), and type ipconfig

# The OSI Model and TCP/IP Model

#### TCP/IP Protocols
A TCP/IP Protocol is a set of rules that governs something within computer communication.
The IETF, or Internet Engineering Task Force, manages these rules and facilitates the open development of them.

> Example: ASCII Protocol
 - ASCII (American Standard Code for Information Interchange) is a internet protocol that you may be familiar with, is a type of character encoding
 - ASCII is a protocol governing how text is represented as binary
 - 128 characters, 95 printable

There are many more protocols, each governing a specific area of how computer communicate.
Ex. ARP, DNS, FTP, UDP, PPP, SAP

We obviously can't cover every protocol, but we'll be talking about a few important ones today.

#### OSI Model
The OSI model, also known as the Open Systems Interconnection Model, helps represent communications between two computers. 

- The OSI model helps coordinate and classify standards
- Each of the many protocols can be classified into one of the seven layers
- Each layer has a function and the protocols in that layer all help with that function

<img src="https://1.bp.blogspot.com/-gdZOMP_8Et4/WTkK6gAKRQI/AAAAAAAACzw/XhDjcUcKGhACYw2URSTEqty4Q7hVOs76ACLcB/s1600/Screen%2BShot%2B2017-06-08%2Bat%2B1.59.05%2BPM.png" style='height: 50%; width: 50%'>

| Layer | Name         | Function                                                                                | Example |
|-------|--------------|-----------------------------------------------------------------------------------------|---------|
| 1     | Physical     | Transport of data between tangible, physical things                                     | DSL     |
| 2     | Data Link    | Device identification and forwarding on a LOCAL network (i.e. home, school)             | PPP     |
| 3     | Network      | Manages identification and path that a device should take, very few of these protocols  | STP     |
| 4     | Transport    | Manages transport of data between computers (delivery method, i.e. fast vs slow)        | UDP     |
| 5     | Session      | Manages connectivity between devices                                                    | SAP     |
| 6     | Presentation | Translates from data sent between computers (binary) to something humans can understand | TLS     |
| 7     | Application  | User Interaction, like resource sharing                                                 | HTTP    |

> Popcorn Hack
 - We just gave an example of a protocol, ASCII, above. What OSI Layer does ASCII fall into?
 - Give another example of a protocol from that layer

#### TCP/IP Model
 - Another method of classifying protocols
 - Simplifies OSI model into four layers
 - Application, Presentation, Session layers are summarised into one Application layer
 - Data Link and Physical layers and summarised into one Link or Physical layer
 - This layer, also known as Network Access, is focused on the transport of bits (1s and 0s) between networks

# Protocols

## DNS - Domain Name Service
- DNS, or Domain Name Service, is a naming system for websites on the internet.
- DNS assigns and has records that relate domain names to ip addresses

#### What is a Domain Name?
 - Domain Names are strings used to identify addresses
 - They map hard to remember IP addresses into simple string of text
 - Would you rather remember 162.159.128.233 or discord.com?
 - Each website has its own IP address that you are sent to when you visit the website
 - https://www.nslookup.io/website-to-ip-lookup/
 - nslookup (website) in command prompt

> Popcorn Hack
 - Open up a command prompt and type "nslookup google.com"
 - You should get 142.250.68.78, we mainly care about the bottom address for now
 - Try visiting that website in your search bar!

#### Subdomains
 - Subdomains are a prefix added to a domain to separate parts of the website
 - There can many subdomains, up to 127, and each can be up to 64 characters long
 - We saw an example of this in our passion projects
 - (SUBDOMAIN).stu.nighthawkcodingsociety.com

#### Domain Name Service Providers
 - DNS Providers manage and sell domain names

<img src="https://blog.hubspot.com/hs-fs/hubfs/what-is-a-domain_3.webp?width=1200&height=735&name=what-is-a-domain_3.webp" style="height: 50%; width: 50%">

> Popcorn Hack
 - List 4 more websites you use often and their IPs
 - What's a subdomain of your passion project backend from last time?
 - What's the domain of your current binary CPT project?

## HTTP vs HTTPS - HyperText Transfer Protocol
HTTP (Hypertext Transfer Protocol) and HTTPS (Hypertext Transfer Protocol Secure) are both protocols used for transferring data over the web. The key difference lies in the security aspect.

HTTP is the standard protocol for transmitting data over the internet. However, it does not provide any encryption, making it susceptible to eavesdropping and unauthorized access. This means that any information exchanged between the user's browser and the website, such as login credentials or personal data, is sent in plain text.

#### HTTPS
On the other hand, HTTPS adds a layer of security by incorporating SSL/TLS (Secure Sockets Layer/Transport Layer Security) encryption. This encryption ensures that the data exchanged between the user and the website is encrypted, making it much more challenging for malicious actors to intercept or tamper with the information.

![image](../../../images/httpvshttpsdiagram.png)

We SSL based encryption last trimester with certbot. Certbot generated SSL certificates for us to ensure HTTPS 
connection between the client and your website. 

![image](../../../images/wireshark_capture.png)

## TCP and UDP - Transmission Control Protocol and User Datagram Protocol

TCP and UDP are both Transport protocols (layer 4 of OSI and layer 3 of TCP/IP). This means they are a set of rules that specify how data is exchanged between devices over the Internet.

#### TCP Packets
What's in a TCP packet?
Packets are a unit of information that are sent over the network. They contain user data, among other identification information.

![image](https://linuxbeans.files.wordpress.com/2016/08/2498f-tcppacketformatdiagram.gif)

#### TCP Handshake
The TCP handshake process - this is how a TCP session is initiated.

Step 1: Client A requests a client-to-server communication session with Server B (SYN)

![image](https://i.ibb.co/xD9sN2V/Image-11-27-23-at-8-34-PM.jpg)

Step 2: Server B acknowledges client-to-server communication session, requests server-to-client communication session (SYN-ACK)

![image](https://i.ibb.co/xgQS4wV/Image-11-27-23-at-8-34-PM-1.jpg)

Step 3: Client A acknowledges server-to-client communication session (ACK)

![image](https://i.ibb.co/gw2WB3h/Image-11-27-23-at-8-34-PM-2.jpg)

After these steps are executed in order, the communication pathway is established between Client A and Server B.

How does TCP actually send the data?

1. Client A wants to send some file to Server B. TCP will first split the data into 6 segments
2. TCP forwards the first 3 segments to the Server B
3. Server B must acknowledge that it has received the segments by sending back an ACK. If Client A doesn't receive the ACK, it resends the segments
4. Client A sends the remaining 3 segments
5. Again, Server B must send back an ACK to confirm it has received the other 3 segments

TCP Session Termination

1. Client A sends segment to server B with the FIN flag to terminate the client-to-server session
2. Server B sends ACK to client A
3. Server B sends FIN to client A to terminate the server-to-client session
4. Client A sends ACK to server B
5. The session closes

![image](https://i.ibb.co/KwHfcj0/Image-11-27-23-at-8-50-PM.jpg" alt="Image-11-27-23-at-8-50-PM)

### UDP
Enough about TCP... what about UDP?

UDP Pros:
- Little cost
- Faster

UDP Cons:
- Little data checking
- Generally unreliable, as no ACK messages are sent
- Packets may arrive out of order or have duplicates/missing packets

UDP sends out all packets at once without any form of handshake or acknowledgement. 

> Popcorn Hack
 - When do we use UDP? While it seems terrible, try to think of some use cases!
 - When might we use TCP?

# Homework Questions
Please answer all of these questions on your personal blog and **explain**. Don't just give an answer. Homework is due Sunday night at 6 pm

#### IP Addresses
1. Which of the following IP Addresses are possible? Explain (yes/no) for each answer choice.
<br>
 - 1.1.1.1.1 No. IP addresses consist of four octets (numbers between 0 and 255)
 - 23.23.23.23 Yes. It follows the correct format for an IPv4 address.
 - 134.492.100.0 No. The second octet should be between 0 and 255.
 - 255.256.55.255 No. The third octet should be between 0 and 255.
 - 2.93.255.19 Yes. It follows the correct format for an IPv4 address.

2. If Dian Du is at home on his home network and sends a message to every computer on the network, what is this an example of? Explain. 
<br>
- Multicast
- Unicast
- Broadcast

Dian Du's message to every computer on his home network is an example of broadcasting. Broadcasting sends data to all devices in the network.

#### Models
1. Three of the four following protocols are on the same layer. Identify which ones and what layer they are on, and why they are on each layer:
    - ASCII (see above for information) ASCII is not a protocol; it's a character encoding standard. It doesn't operate at a specific layer in the OSI model.
    - FTP (facilitates transfer of files over the internet) Application layer. It facilitates file transfer over a network.
    - TLS (see HTTPS section) Transport layer. It provides secure communication over a computer network.
    - USB (permits data exchange between electronics) Physical layer. It defines the cables, connectors, and electrical signals.



2. Telnet is a internet protocol which allows remote access to other computers over a local network or the internet. What layer of the OSI model would this protocol be located on? What is the function of this layer?

Telnet is located at the application layer of the OSI model. This layer is responsible for providing network services directly to end-users or applications.


#### DNS

1. Bob wants to use the domain bob.is.the.best.com. What domain should he buy from a DNS provider (assume it is available)? What would be the subdomains?
Bob should buy the domain best.com from a DNS provider. Subdomains could include bob.is.the.



#### HTTP and HTTPS
1. What is a difference between HTTP and HTTPS?   HTTPS is secure, using SSL/TLS to encrypt the connection, while HTTP is not secure.
<br>
 - What protocol does HTTPS use that HTTP doesn't? HTTPS uses SSL/TLS; HTTP does not.

2. Last trimester we sent HTTP requests for our passion projects
<br>
 - Did we use HTTP or HTTPS?
 - What are the benefits and disadvantages of this?
We used HTTPS because it has more security

#### TCP and UDP

1. Bob is setting up a video streaming service, and he needs the stream to be real time. 
<br>
 - What protocol should he use, TCP or UDP? Why? For real-time video streaming, Bob should use UDP. It is faster but lacks error checking.

 - What are some cons of this protocol? Give an example of a potential issue. Potential issues include packet loss and out-of-order delivery. 


2. TCP has error checking, which ensures that all packets arrive properly. Why is this important? TCP's error checking ensures reliable data transmission.
<br>
 - Give an example of how TCP ensures that there are no errors. If a packet is not acknowledged, TCP will resend it.


3. Server A computer is communicating with Server B. They have already initiated communication and Server A is now attempting to send data to Server B.
<br>
 - How does Server B ensure that they have received any sent packets before Server A continues sending packets in TCP? In UDP?
 Server B acknowledges received packets, ensuring they arrive in order in TCP. Server B does not acknowledge received packets; it's the sender's responsibility in UDP
 - What is another use of this?
 Ensuring data integrity in critical applications.

 IP Addresses
Which of the following IP Addresses are possible? Explain (yes/no) for each answer choice.
1.1.1.1.1: no, ip adresses have 4 octests not 5
23.23.23.23: yes, this is possinle beacese there are 4 coctets and they are in the range of 0-225
134.492.100.0: no because 492 is greater than 256
255.256.55.255: No, because 256 isn’t a possible value for a subnet mask
2.93.255.19: yes this works
If Dian Du is at home on his home network and sends a message to every computer on the network, what is this an example of? Explain.
Multicast
Unicast
Broadcast
Broadcast. A multicast is controllign the suers for which you send the data packet while a unicast is sendign somethign to one person. If you want a message to go out to everyone on a particular network/bandwith, you would use broadcasting.

Models
Three of the four following protocols are on the same layer. Identify which ones and what layer they are on, and why they are on each layer:
ASCII (see above for information)
FTP (facilitates transfer of files over the internet)
TLS (see HTTPS section)
USB (permits data exchange between electronics)
The ASCII regulats what the user cna see, therefore is present on the presentation layer. FTP is on the application layer since it is overseeign the transfer of material bewteen one divice and another. The TLS or HTTP looks at the rules for transferign material acrosss divices. THe UBS however is on another level since it deals witht eh physical matter of trasnfereing things.

When going by the TCP model, UBS would be the one out of place.

Telnet is a internet protocol which allows remote access to other computers over a local network or the internet. What layer of the OSI model would this protocol be located on? What is the function of this layer?
It is on layer 7 or the application model. The reason for this is due to the fact that it helps for the transfereing of information. THe application layer is facilitated with resource sharing and other methods of applying such effects.

DNS
Bob wants to use the domain bob.is.the.best.com. What domain should he buy from a DNS provider (assume it is available)? What would be the subdomains?
The subdomian caould be anything sfter bob. HE should by second level and top level domains.

HTTP and HTTPS
What is a difference between HTTP and HTTPS?
What protocol does HTTPS use that HTTP doesn’t?
HTTP (Hypertext Transfer Protocol) is unencrypted, making data transmission vulnerable to interception. HTTPS (Hypertext Transfer Protocol Secure) uses SSL/TLS encryption for a secure and private connection, ensuring the confidentiality and integrity of data. The key difference is the level of security, with HTTPS providing protection against potential eavesdropping and tampering of information during transmission.

Last trimester we sent HTTP requests for our passion projects.
Did we use HTTP or HTTPS?
What are the benefits and disadvantages of this?
we used https. THe level of security is higher in HTTPS and prevents people from ebign able to tamper with the code as easily. The disadvantage of thsi is that they are very costly and can be very slow, increasign the stree on servers.

TCP and UDP
Bob is setting up a video streaming service, and he needs the stream to be real time.
What protocol should he use, TCP or UDP? Why?
What are some cons of this protocol? Give an example of a potential issue.
EH shoudl use UDP because it is faster, which means less lagging will occur. A con is that the ACK message may not be sent or the packets may be sent out at once. This sould cause the video to completely break in the middle and malfunction. ALso if the server doesn’t acknowledge a connection between the computer and itself, the data could be lost and the computer would ne doing more work than it needed too.

TCP has error checking, which ensures that all packets arrive properly. Why is this important?
Give an example of how TCP ensures that there are no errors.
TCP uses ACK to ensure that all the packets arrived. It sends onyl 3 packets at a time, so if a packet is missing, the computer will know and it will resend the segments. Then the 3 segments will get sent again and the computer needs to respond with an ACK to confirm that the packets were sent correctly.

Server A computer is communicating with Server B. They have already initiated communication and Server A is now attempting to send data to Server B.
How does Server B ensure that they have received any sent packets before Server A continues sending packets in TCP? In UDP?
What is another use of this?
Server B needs to send a message to server A. This message is knonwn as an ACK. Then server A will continue to send to remaining packets. –> TCP

In UDP, the server can send packets even if there isn’t any acknowledgement of a connection. There are no ACK message and no to little data checking. Packets acan slso come out of order and have missing packets. UDP also sends all of its packets at once.

The reason for comparin the two is to show the reliability of the two even though UDP is proved to be cost reductive and faster.
