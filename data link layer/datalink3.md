## HDLC Commands and Responses

Name                               Command/Response                        Description

Information(I)                          C/R                                Exchange User Data
#### Supervisory(S)            
 Receive Ready(RR)                      C/R                                Positive ACK, ready to receive I-frames
 Receive not ready (RNR)                C/R                                Positive ACK, not ready to receive
 Reject(REJ)                            C/R                                Negative ACK, go back N
 Selective Reject(SREJ)                 C/R                                Negative ACK, selective reject
#### Unnumbered(U)
Set normal response/extended mode        C                                 Set mode, extended = 7-bit sequence numbers
Set asynchronous response/extended       C                                 Set mode, extended = 7-bit sequence numbers
Set asynchronous balanced/extended       C                                 Set mode, extended = 7-bit sequence numbers
Set Initialization mode (SIM)            C                                 Initialize link control functions in addressed station
Disconnect (DISC)                        C                                 Terminate logical link connection
Unnumbered ACK (UA)                      R                                 ACK acceptance of one of the set-mode commands
Disconnected Mode (DM)                   R                                 Responder is in disconnected mode
Request disconnect (RD)                  R                                 Request for DISC command
Request initialization mode (RIM)        R                                 Initialization needed, request for SIM command
Unnumbered information (UI)             C/R                                Used to exchange control information
Unnumbered poll (UP)                     C                                 Used to solicit control information
Reset (RSET)                             C                                 Used for recovery, reset N(R), N(S)
Exchange identification (XID)           C/R                                Used to request/report status
Test (TEST)                             C/R                                Exchange identical information fields for testing
Frame Reject (FRMR)                      R                                 Report receipt of unacceptable frame

### HDLC Operation
* Consists of the exchange of I-frames, S-frames, and U-frames 
* Involves 3 phases:
  * Initialization = initializes the data link so that frames may be exchanged in an orderly fashion
  * Data transder = 2 sides exchange user data and the control information to exercise flow and terror control
  * Disconnect = Finally one of the two sides signals the termination of the operation

### Initialization
Either side may request initialization by issuing one of the 6 set-mode commands. This command serves 3 purposes:
1) It signals the other side that initialization is requested
2) It sppecifies which of the 3 modes (NRM, ABM, ARM) is requested.
3) It specifies whether 3- or 7- bit sequence numbers are to be used.

If the other side accepts this request, then the HDLC module on that end transmits an unnumbered ACK (UA) frame back to the initiating side.
If the request is rejected, then a disconnected mode (DM) frame is sent

### Data Transfer

When te initialization has been requested and accepted, then a logical connection is established. both sides may begin to send user data in I-frames, starting with sequence number 0. The N(S) and N(R) fields of the I-frame are sequence numbers that support flow control and error control.
An HDLC module sending a sequence of I-frames will number them sequentially, module 8 or 128, depending om whether 3- or 7- bit sequence numbers are used, and place the sequence number in N(S)>
N(R) is the ACK for I-frames received, it enables the HDLC module to indicate which number I-frame it expects to receive next.

### Data Transfer

* S-frames are also used for flow control and error control
* The receive ready (RR) frame ACK the last I-frame received by indicating the next I-frame expected
* The RR is used when there is no reverse user data traffic (I-frames) to carry an ACK
* Receive not ready (RNR) ACK an I-frame, as with RR, but also asks the peer entity to suspend transmission of I-frames
* When the entity that issued RNR is again ready, it sends an RR. REJ initiates the go-back-N ARQ.
* It indicates that the last I-frame received has been rejected and that retransmission of all I-frames beginning with number N(R) is required
* Selective reject (SREJ) is used to request retransmission of just a single frame

### Disconnect
Either HDLC module can initiate a disconnect
  * either on its own initiative
  * if there is some sort of fault, or
  * at the request of its higher-layer user
HDLC issues a disconnect by sending a disconnect (DISC) frame
The remote entity must accpet the disconnect by replying with a UA and informing its layer 3 user that the connection has been termminated.
Any outstanding unACK I-frames may be lost, and their recovery is the responsibility of higher layers
