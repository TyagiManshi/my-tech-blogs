---
title: "TCP 3-Way Handshake"
seoTitle: "Understanding the TCP Three-Way Handshake"
seoDescription: "Learn about the TCP three-way handshake, a critical process in establishing reliable communication between client and server. "
datePublished: Sat Feb 01 2025 18:30:00 GMT+0000 (Coordinated Universal Time)
cuid: cm724zsw3000d09js4qim44fm
slug: tcp-3-way-handshake
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1738600232117/361d57b7-6170-48f6-aec5-9a3ba0c91c25.webp
tags: internet, networking, chaicode, tcp-handshake

---

A TCP handshake is a process used by the Transmission Control Protocol (TCP) to establish a reliable connection between a client and a server. It ensures that both the sender and receiver are ready to communicate before any data is transferred.

---

The process is commonly referred to as the **Three-Way Handshake**, and it consists of three main steps:

1. ### SYN (Synchronize)
    

The handshake begins with the client sending a **SYN** message to the server. This packet contains a sequence number, which is randomly chosen by the client. This step essentially says, "Hey, I'm here, and I want to establish a connection."

**Client** → SYN: The client sends a TCP packet with the SYN flag set to 1 and a sequence number x (chosen randomly).

2. ### SYN-ACK (Synchronize-Acknowledge)
    

Once the server receives the **SYN** message, it acknowledges the client’s request by sending a **SYN-ACK** packet back. This response contains:

* The server's own randomly chosen sequence number y.
    
* An acknowledgment (ACK) number which is the client’s sequence number incremented by 1 (x+1), indicating that the server has received the initial SYN message.
    
* **Server** → SYN-ACK: The server responds with a SYN and ACK flags set to 1, sequence number y, and acknowledgment number x+1.
    

3. ### ACK (Acknowledge)
    

Finally, the client receives the **SYN-ACK** packet and responds with an **ACK** packet. This packet contains the server’s sequence number incremented by 1 (y+1), acknowledging that the server's message has been received.

* **Client** → ACK: The client sends an ACK with acknowledgment number y+1, confirming that the connection can now be established.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1739378306622/21de230f-ac60-4333-8348-03cf8a76d08e.png align="left")

---

The TCP handshake is essential because it ensures that both the client and server are ready to communicate in a reliable and synchronized manner. It establishes a connection by confirming that both parties are available and prepared to exchange data. The handshake sets up sequence numbers to avoid data loss or errors, ensuring that messages are delivered in the correct order. Additionally, it enables error handling and flow control, preventing one side from being overwhelmed with data. Overall, the handshake lays the foundation for smooth, error-free communication between devices over a network.

---

### Liked the blog? Don’t forget to drop a like ❤️ and share your thoughts in the comments below!