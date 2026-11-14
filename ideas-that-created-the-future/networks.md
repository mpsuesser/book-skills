# Networks

Papers 38 and 41: Cerf and Kahn's internetwork protocol (TCP and the GATEWAY), and Metcalfe and Boggs's Ethernet.

## 38. Cerf & Kahn, *A Protocol for Packet Network Intercommunication* (1974)

**Set out to.** Give a protocol for sharing resources across different packet switching networks. It must provide for:
- variation in packet sizes across networks;
- transmission failures, sequencing, flow control and end-to-end error checking;
- the creation and destruction of logical process-to-process connections.

It also raises the issues of internetwork routing, accounting and timeouts. A **protocol** is "a set of agreed upon conventions", and existing protocols worked only within one network. Their problems are "manifestly compounded when dissimilar networks are interconnected."

**The setting (Fig 38.1).** A network has HOSTS, packet switches and communication media; the switches and media form the **packet switching subnet**. Processes in the HOSTS are the ultimate sources and destinations. The subnet accepts data up to a fixed maximum size with a formatted destination address and routes it store-and-forward.

Networks differ in five ways:
1. addressing, which calls for a uniform addressing scheme;
2. maximum packet size, which calls for either the smallest maximum (impractically small) or reformatting into smaller pieces;
3. time delays, which call for internetwork timing procedures;
4. unrecoverable mutation or loss of data, which calls for end-to-end restoration;
5. status, routing, fault detection and isolation, which call for coordination.

**Design stance.**
- The interface between networks should be "as simple and reliable as possible".
- It should not transform HOST or process protocols; compatible protocols at those levels are needed instead. Requiring every HOST to implement every network's protocol is unacceptable, potentially unbounded.
- So "a common protocol is to be used between HOSTS or processes in different networks and … the interface between networks should take as small a role as possible."
- Each network's internal operation is preserved: networks interconnect as if each were a HOST to the other.
- Charges pass from net to net "until the buck finally stops at the user or his representative."
- The interface is called a **GATEWAY**.

**The GATEWAY (Fig 38.2).**
- **The path:** Process X → NETWORK A → GATEWAY M → NETWORK B → GATEWAY N → NETWORK C → Process Y.
- "The responsibility for properly routing data resides in the GATEWAY."
- A gateway may be built as two halves, each embedding or extracting internetwork packets in its own network's local format.
- X specifies Y's address. Each next gateway is derived from that address, and at each gateway the packet is reformatted for the next network, accounted for, and delivered.

**The packet (Fig 38.3):** LOCAL HEADER (may be null) | SOURCE | DESTINATION | SEQUENCE NO. | BYTE COUNT | FLAG FIELD | TEXT | CHECKSUM.
- The **internetwork header** runs from SOURCE through FLAG FIELD, and the source HOST prefixes it.
- Source and destination uniquely identify every HOST.
- The sequence number and byte count serve sequencing and gateway fault detection, and the flags carry control information such as for duplicate detection.
- The trailing checksum is for end-to-end verification. The gateway does not modify the text, and it forwards the checksum without computing it.

**Fragmentation.** A gateway may split a packet into smaller packets that the destination can piece together.
- The header imposes a minimum size. Fixing a maximum would inhibit growth for three reasons:
  1. it would expose each network's internal packet-size parameters;
  2. raising the maximum with new technology would need every network to agree;
  3. associative addressing and encryption may expand a packet in transit.
- Fragmentation lets packet size vary by network "without global administration" and insulates HOSTS from it. It is best done at the gateway entering the next network, the only place that knows that network's parameters.
- **Reassembly** is the destination HOST's job, not the gateways'. Reassembly at gateways means buffering problems, potential deadlocks, all fragments routed through the same gateway, and delay. It is not enough anyway, since a later gateway may fragment again.
- **Accounting.** Under a fixed charge per packet proportional to packet size, fragments that pass into a network with larger packets cost no more. A larger packet size in one network "will not increase the cost of transmission and may actually decrease it."

**Process-level communication.** Processes exchange full-duplex messages of unbounded but finite length. A **transmission control program (TCP)** in each HOST sends and accepts messages on behalf of its processes, and may break messages into **segments**. Segments are an integral number of 8-bit bytes, which simplifies matters for HOSTS of different word lengths. Multiplexing and demultiplexing are fundamental, and there are two cases.
- **Case 1.** Segments bound for the same TCP form one byte stream that is parceled into packets. "The most critical problem appears to be the amount of interference that processes sharing the same TCP–TCP byte stream may cause among themselves": one missing packet blocks delivery for every process sharing the stream.
- **Case 2.** Every packet carries a **process header**, distinct from the internetwork header, that completely identifies its destination process, and each packet's text goes from a single process to a single process. The destination TCP can then decide on arrival, without other information, which process a packet belongs to and whether it can be delivered.

Only Case 2 avoids interprocess interference, so it is the one chosen.

**Addressing.**
- **Ports.** A **port** designates one message stream associated with a process: "A port address designates a full duplex message stream."
- **TCP addresses (Fig 38.4).** NETWORK (8 bits) | TCP IDENTIFIER (16 bits): up to 256 networks, "sufficient for the foreseeable future", and 65,536 TCPs per network. A gateway checks the destination network: if it is connected to that network, the low 16 bits give the local TCP address; otherwise the high 8 bits select the next gateway.
- **Port addresses** take 16 bits. The sender need not know how they are used: "we do not care how the 16 bits are sliced up by the TCP's involved."

**Formats.**
- **Fig 38.5.** Messages A and B become packets [LH | IH | PH | A₁ | CK], [LH | IH | PH | B₁ | CK], …, with segments from different messages interleaved:
  - LH is the local header, IH the internetwork header, PH the process header, CK the checksum.
  - PH plus text is the segment.
  - IH through CK is the internetwork packet, and the whole is the local network packet.
- **Fig 38.6, the segment** ("merely suggestive"): Source Port (32) | Destination Port (32) | Window (16) | ACK (16) | Text (8n).

**Reassembly and sequencing.**
- **Byte numbering.** Messages from one port are embedded in an infinitely long byte stream. Each byte's sequence number is its position in the stream, and a packet's sequence number is that of the first byte of its text. The byte count covers the text only, and the numbering is unique to the pair of communicating ports (Fig 38.7). The exact position of data is thus known even with pieces missing.
- **Flags (Fig 38.8), 16 bits:**
  - SYN, synchronize to the packet sequence number;
  - REL, release the process or port;
  - ES, end of segment, set by the source TCP on each segment;
  - EM, end of message, set on a segment that holds a whole message or its last part.

  The destination uses ES to find the checksum and EM to know that a message is complete.
- **Fig 38.9, fragmentation by example.** Message A, 1000 bytes starting at byte 100, leaves the source TCP as two segments:

  | Packet | SEQ | CT | ES | EM | Checksum |
  |---|---|---|---|---|---|
  | A₁ | 100 | 500 | 1 | 0 | yes |
  | A₂ | 600 | 500 | 1 | 1 | yes |

  A gateway then splits each in two:

  | Packet | SEQ | CT | ES | EM | Checksum |
  |---|---|---|---|---|---|
  | A₁₁ | 100 | 250 | 0 | 0 | no |
  | A₁₂ | 350 | 250 | 1 | 0 | yes |
  | A₂₁ | 600 | 250 | 0 | 0 | no |
  | A₂₂ | 850 | 250 | 1 | 1 | yes |

  The gateway modifies only SEQ and CT and "need only examine the internetwork header to do fragmentation."

**Retransmission and the window.** "No transmission can be 100 percent reliable." Recovery uses timeouts and positive acknowledgment, with acks carried in the reverse packet stream. The window strategy follows the French CYCLADES network and ARPANET's very-distant-HOST connections.
- **Fig 38.10, the window.** Sequence numbers run from 0 to n − 1. With left window edge a, the window is a … a + w − 1, with w < n, and the sender may transmit up to w bytes without acknowledgment.
- **Fig 38.11, the transmit control block (TCB).** Source Address; Destination Address; Next Packet Seq.; Current Buffer Size; Next Write Position; Next Read Position; End Read Position; No. Retrans./Max Retrans.; Timeout/Flags; Curr. Ack/Window.
- **Sender rules,** with L the left window edge:
  1. transmit bytes from segments whose text lies between L and L + w − 1;
  2. on timeout, retransmit unacknowledged bytes;
  3. on an ack equal to the receiver's left window edge, advance L past the acknowledged bytes.
- **Receiver rules:**
  1. A packet whose sequence number equals the left window edge is acknowledged by sending the next sequence number expected, which acknowledges all bytes in between, and the edge advances.
  2. Packets left of, or outside, the window are discarded, and the current left edge is returned as the ack.
  3. Packets inside the window but not at its left edge, which arrive out of order, are kept or discarded at the receiver's option. The printed text says they "are now acknowledged", which reads like a misprint for "not": an ack names only the left edge.

**Flow control.** Every segment is ultimately acknowledged by returning the sequence number of the next segment to be passed to the process. The ack carries a **suggested window**, the main component of process flow control. The receiver may vary the window by any algorithm, as long as the window never exceeds half the sequence number space.

The scheme is "exceedingly powerful and flexible" and avoids the synchronization troubles of incremental buffer allocation, but it relies heavily on effective retransmission. A receiver that shrinks the window while packets are in flight discards those outside it and restates its window and edge. A sender may occasionally send more than a window, betting that the window will expand.

**Led to.** Sputnik (1957) led to ARPA.
- Paul Baran at RAND (1960) argued that a redundant, distributed, packet-switched network could survive a nuclear attack that crippled the telecommunications grid.
- Licklider (19), after "Man-Computer Symbiosis", speculated about an "Intergalactic Computer Network" and as head of ARPA's IPTO (1964) funded networking generously.
- His successor Robert Taylor started what became ARPANET to give remote access to ARPA-funded computers, and tasked Larry Roberts. Roberts, drawing on Baran and Britain's Donald Davies, settled on packet switching and issued the RFP in 1968.
- Meanwhile IBM, DEC and others built their own networks, with no incentive to agree on a standard that admitted competitors' machines.

Cerf, at UCLA, and Kahn, at BBN, which won the initial ARPANET contract, began collaborating in 1973. Their protocols for connecting networks together turned ARPANET into the internet. The design survives with one major revision: in 1978 what the paper calls TCP was split into **TCP/IP**, with TCP handling reliable end-to-end delivery between hosts on top of IP, simpler and unreliable, which runs on the gateways. Ethernet (41) adopted their gateways and addressing conventions for growth beyond one network. Cerf and Kahn won the 2004 Turing Award, cited in part for "inspired leadership in networking."

## 41. Metcalfe & Boggs, *Ethernet: Distributed Packet Switching for Local Computer Networks* (1976)

**Set out to.** Describe Ethernet, a system for local communication among computing stations. Tapped coaxial cables carry variable-length digital packets among personal minicomputers, printers, large file stores, tape backup, larger central computers and long-haul communication equipment.

**Background (Fig 41.1).** Distributed computing spans a spectrum of decentralization:

| Kind | Separation | Bit rate |
|---|---|---|
| Remote networks | > 10 km | < .1 Mbps |
| Local networks | 10–.1 km | .1–10 Mbps |
| Multiprocessors | < .1 km | > 10 Mbps |

Local networking sits in the middle, combining networking's resource sharing with multiprocessing's parallelism. The product of separation and bit rate, about 1 gigabit-meter per second, is the limit of current technology.
- **Remote networks** grew from terminal-to-computer telecommunications into computer-to-computer networks such as ARPANET. The Aloha Network at the University of Hawaii joined terminals across the islands by packet radio and is now linked to an ARPANET Imp. Networks are growing "down corridors and between buildings".
- **Multiprocessing** is decentralizing for reliability: loosely coupled systems depend less on shared memory and more on "thin wires".
- **Local prototypes** all run at one to three megabits per second: Mitre's Mitrix, Bell Labs' Spider, U.C. Irvine's DCS, and Ethernet.
  - Mitrix and Spider switch through a central minicomputer, while DCS and Ethernet distribute control.
  - Spider and DCS are rings; Mitrix uses two one-way CATV busses; Ethernet is a branching two-way passive bus.

**Construct.** The **Ether** is a shared, branching, passive broadcast medium, named for the luminiferous ether. Each station's **interface** connects bit-serially, through an interface cable, to a **transceiver** that taps the Ether (Fig 41.2: two terminated segments joined by a **repeater**). Ethernet broadcasts "completely-addressed transmitter-synchronous bit sequences called packets onto the Ether and hopes that they are heard by the intended receivers." Every station hears every packet, and destinations copy those whose leading address bits match theirs. This is **broadcast packet switching**, as opposed to store-and-forward routing through intermediate elements.

"Control is completely distributed among stations with packet transmissions coordinated through statistical arbitration."
1. A transmission defers to any already in progress.
2. If interference is detected, the source aborts and reschedules.
3. After an interference-free period, the packet is heard by all and runs to completion.
4. Colliding stations choose random retransmission intervals, whose mean adapts to collision history to keep utilization near optimum.

Even so, packets are "delivered only with high probability."

**Design principles.**
- The design must grow smoothly to several buildings full of personal computers, and it must be inexpensive.
- Distributed control eliminates the reliability problems of an active central controller, avoids a bottleneck, and cuts the fixed costs that make small systems uneconomical.
- It started from the Aloha Network's collision and retransmission. Traffic is bursty, which makes synchronous time-division multiplexing inefficient. "With several innovations of our own, the promise is realized."
- **Topology:** "reliability through simplicity".
  - The Ether is passive, so an active element's failure affects only one station.
  - It is an **unrooted tree**: a tree, so it can branch at a corridor yet keep one path between any two points, avoiding multipath interference; unrooted, so it extends from any point in any direction.
  - Ethernet is the **dual of a star network**. A star has distributed interconnection through many links and central control in a switching node. Ethernet has central interconnection through the Ether and distributed control among stations. Aloha is a star with an outgoing broadcast channel and an incoming multi-access channel; Ethernet is many-to-many over a single broadcast multi-access channel.
- **Control.** Two stations transmitting at roughly the same time is "not only possible but probable". Their overlapping packets **collide** and are abandoned and retransmitted after a dynamically chosen random time, so arbitration is "both distributed and statistical". Controllers adjust the mean retransmission interval in proportion to the frequency of collisions. Cooperation is required: a station could usurp the Ether with a fixed short interval or very large packets, and low-level software prohibits that.
- **Addressing.** The header carries source and destination. A zero destination is a wildcard matching every station: a **broadcast packet**.
- **Reliability.** "An Ethernet is probabilistic." Packets can be lost to interference, impulse noise, an inactive receiver or purposeful discard. Ethernet gives **best efforts**, and processes at the ends take the precautions they want. Declining to guarantee any single packet buys economy and high reliability averaged over many packets, and it puts error recovery "where it will do the most good".

**The five mechanisms.** The tap must disturb transmission as little as possible, and "the design of the transceiver must be an exercise in paranoia"; removing its power should disconnect it.
1. **Carrier detection.** Bits are phase encoded, so there is at least one transition per bit time and the presence of carrier is visible.
   - **Deference:** no station starts while it hears carrier. Aloha lacks this, so its collision rate is higher and its efficiency falls with packet length; with carrier detection, efficiency rises with packet length.
   - **Acquisition:** once a transmission has run for one end-to-end propagation time, every station hears it and defers, and it completes without collision.
   - Collisions therefore happen only when two stations start within a propagation time of each other, almost always just after a transmission they were both deferring to. Deferring stations do not randomize, so they pile on, collide, randomize and retransmit.
2. **Interference detection.** The transceiver notices a difference between the bit received and the bit being transmitted. That gives three advantages:
   - the station knows at once that the packet is damaged and need not wait out a long acknowledgment timeout;
   - interference lasts at most one round trip, whereas Aloha collisions run to completion;
   - the frequency of detected interference estimates the traffic load.
3. **Packet error detection.** A checksum is appended on transmission and recomputed on receipt, and inconsistent packets are discarded.
4. **Truncated packet filtering.** Collisions leave fragments of only a few bits, which are filtered in hardware.
5. **Collision consensus enforcement.** A station that detects interference momentarily jams the Ether so that every participant detects it and aborts.

**Implementation.** The experimental system has a 1-kilometer Ether, runs at 3 megabits per second, and serves 256 stations. These figures come from the environment and "what would be marginally achievable", and are not hard limits.
- The dominant station is the Alto. 3 Mbps is well below its path to main memory, which reduces special-purpose buffering.
- **Fig 41.3, the packet:** SYNC (1 bit) | DEST ADDRESS (8) | SOURCE ADDRESS (8) | DATA (~4000 bits) | CHECKSUM (16).
- **Ether:** low-loss coaxial cable with off-the-shelf CATV taps and connectors; the cable's cost is insignificant.
- **Transceivers** must drive a kilometer tapped by 256 stations at 3 Mbps.
  - They must survive sustained shorts, improper termination and simultaneous drive by all 256 stations, and tolerate ground differentials and everyday noise.
  - They are powered and controlled over the interface cable's twisted pairs, and an unpowered transceiver disconnects; a watchdog timer shuts down the output stage if it behaves suspiciously.
  - "Here is where our fight for reliability is won or lost; a broken transceiver can, but should not, bring down an entire Ethernet."
- **Interface:** one per kind of station.
  - Transmitting, it serializes and phase-encodes 16-bit words between a start bit (SYNC) and a CRC.
  - Receiving, carrier marks the start, SYNC acquires bit phase, and words are deposited in the buffer until carrier stops; the interface then checks for an integral number of words and a correct CRC.
  - Hardware address filtering spares the software.
- **Controller (Fig 41.4).** Retransmission intervals are multiples of a **slot**: the maximum time between starting to transmit and detecting a collision, one end-to-end round trip.
  1. A new packet starts with a zero load estimate.
  2. If the load estimate has overflowed, report an error.
  3. Otherwise generate a random number, weight it by the load estimate, and count it down.
  4. Transmit when the Ether is silent. Success is done; a timeout is an error; a collision increases the load estimate and returns to step 2.

  The mean interval starts at one slot and doubles with each collision, which approximates **Binary Exponential Backoff**. Under light load the mean seldom departs from one slot; under heavy load "retransmission traffic backs off to sustain channel efficiency."

**Growth.**
- **Signal cover:** a simple unbuffered **packet repeater** joins segments. The authors operate a two-segment system but hope not to rely on repeaters, since a repeater failure partitions the Ether.
- **Traffic cover:** a **packet filter** passes a packet to another segment only if its destination is there.
- **Address cover:** beyond 8-bit addresses, **packet gateways** and software addressing conventions (Cerf and Kahn, 38) extend addressing down into stations (ports, processes) and up into internetworks.
- **The rule:** only one repeater or filter may join two segments, because a packet repeated by several would interfere with itself. Gateways are unlimited, since each repeats only packets addressed to it, and a gateway failure need not partition the network if other paths exist.

**Performance.** In the model, the Ether alternates between transmission intervals and contention intervals made of slots. A slot is empty (no attempt), a collision (more than one) or an acquisition (exactly one).
- **Symbols:** P is bits per packet, C the peak capacity in bits per second, and T the slot time. Q stations are continuously queued, and each queued station attempts in a slot with probability 1/Q, the optimum decision rule, which the load-estimating algorithm approximates.
- **Acquisition probability:** A = Q · (1/Q) · (1 − 1/Q)^(Q−1) = (1 − 1/Q)^(Q−1).
- **Mean waiting time,** in slots: waiting i slots has probability A(1 − A)^i, so W = (1 − A)/A.
- **Efficiency,** the fraction of time carrying good packets: E = (P/C) / ((P/C) + WT).
- For packets above 4000 bits, efficiency "stays well above 95 percent". For packets about the size of a slot it approaches 1/e, the asymptotic efficiency of slotted Aloha.

**Protocol.** The Ether control protocol does packet framing, error detection, addressing and multi-access control. Error correction, flow control, process naming, security and accounting belong to higher-level protocols on top.
- **Terminology** uses orthogonal pairs. A packet has a source and destination; a flow of data has a sender and receiver; a connection has a listener and initiator; a service has a server and user.
- **EFTP,** the Ethernet File Transfer Protocol, is easy to understand and implement correctly, and it has "dutifully carried many valuable files".
- **Fig 41.5, an EFTP packet,** in 16-bit words: Destination | Source; Packet Type; Sequence Number; Length (in words); Data; Software Checksum.
  - Only data packets carry Length and Data.
  - There are five types: data, ack, abort, end and endreply.
  - "It is more advisable to err on the side of spacious fields; try as you may, one field or another will always turn out to be too small."
  - The software checksum is a 1's-complement add-and-cycle over the whole packet. It backs up the hardware CRC and protects the station's parallel data paths. All 1's, an impossible value, means no checksum was computed.
- **Data transfer.** Data packets are numbered from 0 and retransmitted periodically until a matching ack arrives.
  - The receiver acks, accepts and increments on the expected sequence number.
  - It acks and discards a packet one less than expected, presuming its earlier ack was lost.
  - It ignores everything else.
- **End-dally.**
  1. The sender sends an end packet with the next sequence number.
  2. The receiver replies with endreply and **dallies** for 10 seconds.
  3. The sender echoes the endreply and leaves.
  4. The dallying receiver gets the echo and leaves too.

  Any lost packet is covered by a timeout, which makes it "practically certain" that both agree the file arrived. An abort packet is the polite way to give up.
- **Shortcomings of EFTP.**
  1. It transfers files station to station within one network only, not process to process or through gateways.
  2. Process rendezvous is degenerate.
  3. There is no real flow control.
  4. It carries only integral 16-bit words of unnamed files.
  5. The receiver is always also the listener and server.

**Conclusion.** "Our emphasis on distributed control was well placed." Minimal, passive shared components give "a very high level of reliability", and broadcast packet switching proved flexible.

**Led to.** Networking is tricky: flawless delivery over failure-prone links among potentially hostile nodes, with time dependencies and special-purpose hardware that is hard to verify. Small computers on local networks of disparate hardware compound the problem.

Metcalfe went to graduate school at Harvard as universities joined ARPANET (38). Harvard resisted his offer to run its connection, so he did the job at MIT instead, and he failed his first PhD defense; the degree came after a revised thesis. At Xerox PARC, where the Alto, the first networked personal computer, was being developed, he learned of the Aloha Network. "The solution to the subtleties of interconnecting computers with wires was to relax control": a common coaxial cable with a physical tap, a spike driven into the copper core at any convenient spot. Stations dump packets onto the passive cable, the packets spread both ways, and each station listens for its own. David Boggs, a young radio engineer at PARC, brought wireless expertise.

The name stuck. The passive network and Xerox's low licensing fees made Ethernet the ubiquitous standard, and both men became successful entrepreneurs.
