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

#### HDLC Data Transfer Modes
* Normal response mode (NRM)
 * Used with an unbalanced configurationo
 * Primary initiates transfer
* Asynchronous Balanced Mode (ABM)
 * Used with a balanced configuration
 * Either station initiates transmission
 * Has no poling overhead
 * Most widely used
* Asynchronous Response Mode (ARM)
 * Used with unbalanced configuration
 * Secondary may transmit without permission from primary
 * Rarely Used

#### Address Field

Address field identifies secondary station that transmitted or will receive frame and is usually 8 bits long. It may be extended to multiples of 7 bits so leftmost bit indicates if it is the last octet (1) or not (0). For example, the address 11111111 allows a primary to broadcast a frame for reception by all secondaries.

#### HDLC Frame Structure

##### HDLC defines 3 types of frames, each with a different control field format.
Information frames (I-frames) = carries the data to be transmitted for the user. The flow and error control data, using the ARQ mechanism, are piggybacked on an information frame

Supervisory frames (S-frames) = provide the ARQ mechanism when piggybacking is not used.

Unnumbered frames (U-frames) = provide supplemental link control functions

#### Control field
* Use of poll/final (P/F) bit depending on context
* In command frames P bit is set to 1 to solicit (poll) a response from the peer HDLC entity
* In response frames F bit is set to 1 to indicate the response frame transmitted as a result of a soliciting command
* The basic control field for S- and I-frames uses 3 bit sequence numbers
 * An extended control field can be used that employs 7-bit sequence numbers

U-frames always contain an 8-bit control field

#### Information and Frame Check Sequence (FCS) Fields
##### Information Field

Present only in I-frames and some U-frames, must contain an integral number of octets and variable length.

##### Frame Check Sequence Field (FCS)

Error detecting code calculated from the remaining bits of the frame, exclusive of flags. The normal code is the 16-bit CRC-CCITT. Optional 32-bit FCS, using CRC-32, may be employed if the frame length or the line reliability dictates this choice.


[[Page 1]](https://github.com/changherng/Encoding/blob/main/data%20link%20layer/Datalink.md) [Page 2] [[Page 3]]
