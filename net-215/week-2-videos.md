# Week 2 Videos

## Layered Models

Protocol Suite - A set of protocols designed to work together

Layering Model - An abstraction that separates protocols based on function rather than implementation.&#x20;

Protocol Model - Model closes matches the structures of a suite.

Reference Model - Describes what has to be done at a particular layer, but does not prescribe how it should be done. Tells you how it works, but not exactly? OSI Model.

Benefits of a layered model

* Assists in protocol design; only focus on a particular layer when designing a protocol
* Fosters competition and collaboration
* Prevents tech and capability changes from affecting others
* Provides a common language.

Common Layered Models are the OSI and TCP/IP Models.





Protocols fit inside the layered models.&#x20;

## OSI Model

OSI - 7

* Application
* Presentation
* Session&#x20;
* Transport
* Network
* Data Link
* Physical

TCP / IP (4)

* Application
* Transport
* Internet
* Network Interface

### Application

Closest to end user

HTTP, file transfer, users interact directly, SMB, etc

### Presentation&#x20;

Presents data for the application for the network. Encryption or decryption and encoding and decoding is a good example

### Session

Setup, coordination, of a connection. Starting and ending a connection.

### Transport

Providing for cocmmunication from an application on one computer to another. Controlling maximum rate, avoiding network congestion. (Ports?)

### Network

How communication crosses the internet, logical addressing like IP address. and how packets are forwarded and routed.

### Data Link

MAC addresses.

### Physical

RAHHHHH 0101010101.

### Why does it matter?

Visual description of a particular networking system. Helps narrow down your problems.&#x20;

## Packets Headers

Data moves up and down the layers. Each layer has a protocol that ensures the message arrives as expected. The sender adds some extra information to the packet, known as a header. It adds it to the front, which is why it is called a header.

Encapsulation - Only added to the beginning in networking.

