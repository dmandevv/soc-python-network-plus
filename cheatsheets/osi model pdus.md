# OSI Model — Protocol Data Units (PDU) by Layer

| Layer | Name | PDU |
|---|---|---|
| 7 | Application | Data |
| 6 | Presentation | Data |
| 5 | Session | Data |
| 4 | Transport | Segment (TCP) / Datagram (UDP) |
| 3 | Network | Packet (also called Datagram for connectionless protocols like IP/UDP) |
| 2 | Data Link | Frame |
| 1 | Physical | Bit |

- Layers 5-7 are generally just referred to as "Data" (no distinct PDU name tested).
- "Datagram" can appear at both Layer 3 (IP) and Layer 4 (UDP) depending on context — common source of confusion.
