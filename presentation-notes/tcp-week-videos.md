# TCP Week Videos

## TCP Intro

* IP uses Best-Effort Delivery
  * Doesn't really care if anything fails; just tries to get you to the destination
  * IP just drops packets if the network is congested
* TCP - Transmission Control Protocol
  * Guarantees prompt and reliable comms
  * Data is delivered in the same order that it was sent
* 3 Features
  * Application must request a connection
  * Point-to-point communication: To Endpoints
  * Complete Reliability: Ensures that data is complete and in order
  * Full Duplex Communication: can flow in both directions at the same time
* TCP Header
  * Source and Destination Port
    * Source: What app sent the packet
    * Destination: What app is to receive the packet
  * Sequence and Acknowledgement
    * 32-bit numbers to keep track of comms
    * Sequence is what is being sent in the direction
    * Acknowledgment: what has been received.
* TCP Flags:
  * 1 means the flag is set; 0 means the flag isn't.
  * URG: Bit 106
  * ACK: 107
  * PSH: 108
  * RST: 109
  * SYN: 110
  * FIN: 111
* TCP Features
  * 3-way handshake
  * Sequencing
  * Reliability

<figure><img src="../.gitbook/assets/image (148).png" alt=""><figcaption></figcaption></figure>

## TCP 3 Way Handshake

* TCP 3-way exchange to ensure unambiguous agreement.
* Step 1
  * SYN - Synchronization
* Step 2
  * SYN / ACK - Acknowledgment and SYN to start the session
* Step 3
  * ACK - From client back to the server

<figure><img src="../.gitbook/assets/image (146).png" alt="" width="563"><figcaption></figcaption></figure>



*   Shutdown Process

    * Graceful Connection Shutdown
    * FIN flag used to close a connection
    * FIN and ACK together.

    <figure><img src="../.gitbook/assets/image (147).png" alt="" width="563"><figcaption></figcaption></figure>



## TCP Sequence Numbers

* Requires each end to generate a random 32-bit sequence number per direction
* Random to avoid someone stealing a session
* Sequence number is what the receiver expects, and the acknowledgement number is what the server expects from the client.
  * Both numbers increment.
* ACK packets don't consume a sequence number
* TCP increments the SEQ # by the number of **bytes sent in the last packet.**
  * Built-in error detection, can indicate dropped or missing packets.
* ACK just acknowledges what has been received so far, doesn't have to be sent for every packet received.
  * If an ACK packet is not received, there is a retransmission

<figure><img src="../.gitbook/assets/image (149).png" alt="" width="563"><figcaption></figcaption></figure>

## TCP Sliding Windows

* Reliability and Flow Control
* If a message is dropped, then an ACK is never sent.&#x20;
* Sliding Windows
  * Window Size Header, 16-bit receive window.
  * A limit to # of bytes that can be received.
* Receiver acknowledges a reduced window size. Sliding window; can grow and shrink based on demand.
  * Improves efficiency and reliability&#x20;
* Server size is usually smaller; clients are larger.
* Zero value for window size when buffer is full
  * Window update packet when&#x20;

## Window Scale Factor

* On larger networks, 16-bit window size may be too small
* TCP Option called the scale factor
* Set in the SYN headers of the handshake.
* Window Scale = 2^x. So 7 = 2^7, multiply Window size by 128.

## Adaptive Retransmission

* Timers, the stopwatch, how long it waits for an ACK before it realizes a packet is lost.
* Monitors and reacts quickly.&#x20;
* Fixed timeout would not work well for the internet, they are adaptive for TCP.
* Round trip times (RTT)
  * TCP uses a statistical function to make an exponentially weighted moving average of RTT to reset the transmission timer.&#x20;
* Estimate Round Trip Delay, records the time a message is sent.
* Works well when there is a constant delay, or when delays start to vary.

