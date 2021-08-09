## NRZ (Non return to zero)

The most straightforward form of digital modulation is to use a positive voltage to represent a 1 and a negative voltage to represent a 0. For an optical fiber, the presence of light might represent a 1 and the absence of light might represent a 0. This scheme is called NRZ (Non-Return-to-Zero).
`An example is shown in Fig. 2-20(b).`
`Once sent, the NRZ signal propagates down the wire. At the other end, the receiver converts it into bits by sampling the signal at regular intervals of time.`

This signal will not look exactly like the signal that was sent. It will be attenuated and distorted by the channel and noise at the receiver. To decode the bits, the receiver maps the signal samples to the closest symbols. For NRZ, a positive voltage will be taken to indicate that a 1 was sent and a negative voltage will be taken to indicate that a 0 was sent.


### Why
NRZ is a good starting point for our studies because it is simple, but it is seldom used by itself in practice. More complex schemes can convert bits to signals that better meet engineering considerations.


### Problems
The receiver may lose synchronization (attenuation) when using NRZ to encode a synchronous link which may have long runs of consecutive bits with the same value (no changes in voltage). Other problems with NRZ include; Data sequences containing the same number of 1's and 0's will produce a DC level, and NRZ requires a large bandwidth, from 0Hz (for a sequence containing only 1's or only 0's) to half of the data rate (for a sequence of 10101010).


