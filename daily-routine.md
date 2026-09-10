# Daily Routine

A guide, not a syllabus. Sources, rankings, and free-tier notes live in **[practice-resources.md](practice-resources.md)** — this file only says **what to work on and where each track currently stands.**

Claude follows this file to pick up where things left off, and updates *Where things stand* as blocks are completed.

## The shape of a day

**The blocks are a continuous loop, not a daily reset.** Work down the list in order; a day ends wherever it ends, and the next session picks up at the **next** block. After block 4 it wraps to block 1.

```
  1  Network+  →  2  Packet Tracer  →  3  Homelab  →  4  Homelab audit
  ↑                                                                  │
  └──────────────────────────────────────────────────────────────────┘
```

| Block | Track | Source |
|---|---|---|
| **1** | Network+ — one objective section | The walkthrough in `objectives/` |
| **2** | **Packet Tracer** — one scenario, built and verified | Queue below |
| **3** | **Homelab — 2 hours** | The build itself. See [soc-python-homelab](https://github.com/dmandevv/soc-python-homelab) |
| **4** | **Homelab audit** — Network+ concepts on real gear | Queue below |

**Restructured 2026-09-10 around one goal: mostly hands-on learning of the Network+ material.** Blocks 2 and 4 are both practice, on simulated and real gear respectively — and block 4 is the one that didn't exist before.

**⚠️ Blocks 3 and 4 are both lab work, and they are both at the end on purpose.** The lab needs no discipline; it would happily consume a whole day. Blocks 1 and 2 are the ones that only happen if they come first.

- **The lab does not open until 1 and 2 are done in the current pass.** Short blocks are fine; skipped ones are not.
- **The three-day skip trigger applies to blocks 1 and 2 only.** Avoidance is not the lab's problem.

**⚠️ Do not restart at block 1 each session.** The *Where things stand* table below records where the last session stopped — start at the block **after** it.

## Where things stand

**Last session ended after block 1** (2026-09-10). **Resume at block 2.**

| Track | Position | Next |
|---|---|---|
| **Network+** | **4.2 in progress.** Covered: DoS/DDoS, VLAN hopping, MAC flooding, ARP poisoning/spoofing, DNS poisoning/spoofing | **4.2 remainder** — rogue DHCP and APs, evil twin, on-path, social engineering, malware. Then 4.3, then a quiz on all of 4.0 |
| **Packet Tracer** | **2 scenarios done** — STP, and double tagging. NAT scrapped | **Scenario 3 — OSPF, single area** |
| **Homelab** | **Phase 1 complete + VLAN 50 sandbox + bastion.** Console abandoned as a display; MAC-connect narrowed; NUT verified | **RA Guard** on the bridge ports, then the **syslog collector** |
| **Homelab audit** | **Not started** | **Audit 1 — map the network from observed state** |

## Block 2 — Packet Tracer scenario queue

**One scenario per entry, each finishable within two blocks**, drawn from the N10-009 objectives and chosen for things the homelab cannot demonstrate — redundancy, dynamic routing, and failure behaviour need more devices than one switch provides.

**⚠️ Exam practice, not homelab modelling.** Each scenario gets its own `.pkt` file. Mixing the two is what made the NAT attempt confusing.

| # | Scenario | Objective | Status |
|---|---|---|---|
| **1** | ~~NAT and PAT~~ | 2.1 | **Scrapped** — the 3560 cannot translate |
| **2** | **Spanning Tree** | 2.2 | ✅ **Complete.** 9 lost pings on PVST+, **zero on RSTP** |
| **2b** | **VLAN double tagging** | 4.2 | ✅ **Complete.** Untagged native hop observed and closed. Attack itself not reproducible in Packet Tracer |
| **3** | **OSPF, single area.** Three routers, convergence observed, then a link cut and re-converged | 2.1 | **Next** |
| **4** | **EtherChannel / LACP.** Aggregate two links, verify distribution, fail one member | 2.2 | Queued |
| **5** | **First-hop redundancy (HSRP).** Two gateways, one virtual address, failover from a host | 2.1 | Queued |
| **6** | **DHCP relay.** Central server, remote VLANs, `ip helper-address`, giaddr read in the capture | 3.4 | Queued |
| **7** | **IPv6 and SLAAC.** Dual-stack a segment, watch RA and DAD, compare with DHCPv6 | 1.7 / 3.4 | Queued |
| **8** | **VLSM and summarisation.** Three sites, one block, subnet by hand then summarise | 1.7 | Queued |
| **9** | **Wireless channel planning.** Three APs, non-overlapping channels, co-channel interference | 2.3 | Queued |
| **10** | **QoS.** Voice prioritised over bulk traffic across a congested link | 2.1 | Queued |

## Block 4 — Homelab audit queue

**Added 2026-09-10.** Where block 2 builds a scenario to learn a concept, this one **goes looking for the concept in a network that already exists** — and checks whether it is doing what the documentation claims.

**Two things make this worth a block of its own:**

- **The gear is real**, so the answers are not a simulator's opinion. Duplex mismatches, error counters, and CPU ceilings exist here and not in Packet Tracer
- **It finds drift.** Five documentation errors turned up in one week by accident. Looking on purpose will find more

| # | Audit | Objectives | Status |
|---|---|---|---|
| **1** | **Map the network from observed state.** ARP tables, bridge host table, `/ip route`, neighbour discovery — build the topology from what the switch says, then diff it against `network-diagrams.md` | 1.6, 3.1 | **Next** |
| **2** | **Re-verify the firewall policy matrix.** Test every cell of the table in `network-diagrams.md` in both directions. Three days of changes have gone in since it was written | 4.3 | Queued |
| **3** | **VLAN and trunk audit.** Bridge VLAN table, PVIDs, tagged/untagged per port. Find any port not doing what `ip-plan.md` claims | 2.2 | Queued |
| **4** | **Trace one packet end to end.** Desktop → website VM, naming every table consulted: ARP, bridge host, routing, firewall chain, NAT. **The single best OSI exercise available** | 1.1, 2.1 | Queued |
| **5** | **Layer 1 health.** Interface counters, CRC and FCS errors, duplex and speed on every active port. Errors accumulate silently and only show up as "the network is slow" | 5.2 | Queued |
| **6** | **DHCP lifecycle on the wire.** Capture a real DORA exchange, read the options, T1/T2, and the lease table | 3.4 | Queued |
| **7** | **DNS path audit.** Who resolves for whom, what is cached, where queries actually go. Feeds the Phase 3 logged-resolver plan | 3.4 | Queued |
| **8** | **Re-measure throughput.** `iperf3` across VLANs against the recorded **251 Mbps single flow / 468 Mbps across four**. Confirm the CPU ceiling still holds after this week's rule changes | 5.4 | Queued |
| **9** | **Spanning tree on real hardware.** RSTP state on the CRS326 — root bridge, port roles, and why a single-switch topology still runs it. Contrast with the Packet Tracer lab | 2.2 | Queued |
| **10** | **IPv6 exposure audit.** Is it running unintentionally? Link-local addresses, Router Advertisements, and what a rogue RA would reach. Directly feeds the Phase 2 RA Guard task | 1.7, 4.2 | Queued |

## Parked tracks

**Not deleted — parked with their position, so they can be resumed.**

| Track | Position when parked | Why |
|---|---|---|
| **TryHackMe** | TShark room complete. SOC Fundamentals turned out to be premium | Parked 2026-09-10. **Nmap Live Host Discovery** (`nmap01`) is the next room if it returns. Use [tryhackme.com/free-rooms](https://tryhackme.com/free-rooms) — third-party free-room lists are stale |
| **Packet analysis** | **3 complete** — *First to Last*, *Easy as 123*, *Lumma in the Room-ah!* (all answers correct). Tradecraft in [analysis-lessons.md](analysis-lessons.md) | Parked 2026-09-10. Next would be ***It's a trap!*** (2025-06-13). **This is the SOC-analyst track rather than the exam track** — worth restarting after the exam |

## Progression triggers

| When | Change |
|---|---|
| **Network+ objectives finish** | Block 1 becomes practice exams |
| **The Packet Tracer queue empties** | Block 2 becomes **Containerlab**, or folds into a RouterOS CHR lab on Proxmox |
| **The audit queue empties** | Block 4 restarts from audit 1 — the answers change as the lab grows, and that is the point |
| **Phase 2 telemetry exists** | Block 4 gains real detection work rather than configuration review |
| **A block in 1-2 is skipped three days running** | Replace it. A track being avoided is not being learned |

## Why the lab blocks come last

It previously competed with these hours and lost, which is the wrong way round. **Simulated work was a rehearsal for the lab; the lab is the thing itself.**

**⚠️ It still has no security telemetry**, so there is nothing to investigate — the switch's logs live in RAM and rotate away within hours. **Building the collection layer is the work**, and it is what makes SOC practice possible later. Start with syslog off the switch: everything else builds on top of it.
