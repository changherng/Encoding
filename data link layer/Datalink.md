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
