# Data Link
### Data Link Control Protocols
* Control and Manage the excange of data over a data communication link
* Requirements for effective data communication between two connected stations
  * Frame Synchronization
  * Flow Control
  * Error Control
  * Addressing
  * Control and data
  * Link Management
### Frame Synchronization/ Frame Detection
Data link layers transmits and receives strings of bits to/from the physical laters
How to identify a frame from the bit strings
* Time based
  * Specifies and amount of time between frame
* Character count
  * Introduced a count of remaining characters in the frame's header
* Flag bytes with byte stuffing 
  * Byte stuffing modified the frame with a special byte sequence such as STX and succeeds it with ETX.
* Starting and ending flags, with bit stuffing.
### Flow Control
To assure that a transmitting node does not transmit more data a receiver can receive:
  * The receiving entity typically allocates a data buffer of some maximum length for a transfer
  * When data are received, the receiver must do a certain amount of processing before passing the data to the higher-level software.
Without flow control, the receiver's buffer may fill up and overflow while it is processing old data.
### Frame Transmission Model
* Send-receive relationship
* Each arrow represents a single frame transiting a data link between two stations.
* Data are sent in a sequence of frames, with each frame containing a portion of the data and some control information (Sequence no.)
* The time it takes for a station to emit all of the bits of a frame onto the medium is the transmission time.
### Stop-and-wait flow control
* Simplest form of flow control
 * Source transmit frame -> Destination receives frame and replies with Acknowledgement -> Source waits for ACK before sending new frame -> Destination can stop flow by not sending ACK to source.
* Source will break up a large block of data into smaller blocks and transmit the data in many frames
 * The buffer size of the receiver may be limited
 * The longer the transmission, the more likely an error may occur, causing retransmission of the entire frame
 * On a shared medium it is usually desirable not to permit one station to the medium for an extended period, thus causing long delays at the other sending station
### Sliding windows flow control
* Allows multiple numbered farmes to be in transit
 * Receiver has buffer W long
 * Transmitter sends up to W frames without ACK
 * ACK includes number of next frame expected
 * Sequence number is bounded by size of field (k)
  * Frames are numbered modulo 2^k
  * Giving max window size of uo to 2^(k)-1
 * Receiver can ACK frames without permitting further transmission (Receive not ready)
 * Must send a normal ACK to resume
* If have full-duplex link, can piggyback ACKs.
### Error control
* Lost frames - a frame fails to arrive at the other size
* Damaged frames -  frame arrives but some of the bits are in error

Error detection > Positive ACK > Retransmission after timeout > Negative ACK and retransmission

[Page 1]
[[Page 2]](https://github.com/changherng/Encoding/blob/main/data%20link%20layer/datalink2.md)
