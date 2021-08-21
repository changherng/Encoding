### Automatic Repeat Request (ARQ)
* Collective name for error control mechanisms
* Effect of ARQ is to turn an reliable data link to a reliable one

Versions of ARQ
Stop-and-wait , Go-back-N ,  Selective-reject

### Stop-and-wait ARQ
Source will transmit a single frame and wait for ACK, during this, no other data can be sent until destination's reply arrives (ACK). If frame received is damaged, discard it. If the transmitter has timeout and if no ACK is received within timeout, retransmit frame. If ACK sent is damaged. transmitter will not recognize and retransmit, if the receiver gets two copies of the same frame, it will use alternate numbering and ACK0/ACK1.

### Go-Back-N ARQ
* Most commonly used error control
* Based on sliding-window
* Use window size to control number of outstanding frames

While no errors occur, the destination will acknowledge incoming frames as usual
  * RR - receive ready, or piggybacked ACK
If the destination station detects an error in a frame, it may send a negative ACk
  * REJ - reject
  * Destination will discard that frame and all future frames until the frame in error is received correctly.
  * Transmitter must go back and retransmit that frame and all subsequent frames.
### Selective-Reject ARQ
Also called selective retransmission since only rejected frames are retransmitted. Subsequent frames are accepted by the received and buffered. This helps to minimize retransmittion. However, the receiver must maintain large enough buffer.
* More complex logic in transmitter
  * Less widely used
* Useful for satellite links with long propagation delays.

### High Level Data Link Control (HDLC)
#### Most important data link control protocol

ISO 3009, ISO 4335 (Both basis for other data link control protocols)
#### Station types

Primary - controls operation of link
Secondary - under control of primary station
Combined - issues commands and responses

#### Link configurations

Unbalanced - 1 Primary, multiple secondary
Balanced - 2 combined stations
