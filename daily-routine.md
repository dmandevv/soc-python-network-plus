# Daily Routine

A guide, not a syllabus. Sources, rankings, and free-tier notes live in **[practice-resources.md](practice-resources.md)** — this file only says **what to work on today and where each track currently stands.**

Claude follows this file to pick up where things left off, and updates *Where things stand* as blocks are completed.

## The shape of a day

**The blocks are a continuous loop, not a daily reset.** Work down the list in order; a day ends wherever it ends, and the next session picks up at the **next** block. After block 5 it wraps back to block 1.

```
  1  Network+  →  2  TryHackMe  →  3  Network topics  →  4  Packet analysis  →  5  Homelab (2h)
  ↑                                                                                        │
  └────────────────────────────────────────────────────────────────────────────────────────┘
```

| Block | Track | Source |
|---|---|---|
| **1** | Network+ — one objective section | The walkthrough in `objectives/` |
| **2** | **TryHackMe** — free rooms | [tryhackme.com](https://tryhackme.com) |
| **3** | **Network topics** — one scenario, built and verified | Packet Tracer. Queue below |
| **4** | Packet analysis | malware-traffic-analysis.net |
| **5** | **Homelab — 2 hours** | The build itself. See [soc-python-homelab](https://github.com/dmandevv/soc-python-homelab) |

**The order is deliberate, and the reason is motivational rather than technical.** The homelab is the part that needs no discipline — it would happily consume a whole day on its own. Everything above it is necessary and comparatively dull. **Putting the lab last makes it the thing the other four blocks are paid for**, which is the only arrangement where the studying reliably happens.

**⚠️ The failure mode to watch is the opposite of what a fixed order usually risks.** Block 5 will not get skipped. The danger is block 5 starting at 10am — the homelab quietly annexing the day, and blocks 1-4 becoming something that happens tomorrow.

Two guards, both worth keeping:
- **The lab does not open until 1-4 are done in the current pass.** Not a rule about effort, just about order. Short blocks are fine; skipped ones are not.
- **The three-day skip trigger applies to blocks 1-4 only.** If one of them goes three days untouched, it gets replaced — the homelab is not a candidate for that trigger, because avoidance is not its problem.

**⚠️ Do not restart at block 1 each session.** Changed 2026-09-09, having briefly been the rule. A daily reset meant blocks 4 and 5 were reached only on long days; a continuous loop reaches every block at the same rate regardless of how long any one day runs. **The *Where things stand* table below records where the last session stopped — start at the block after it.**

## Where things stand

**Last session ended after block 1** (2026-09-10). **Resume at block 2.**

| Track | Position | Next |
|---|---|---|
| **Network+** | **4.2 in progress.** Covered: DoS/DDoS, VLAN hopping, MAC flooding, ARP poisoning/spoofing, DNS poisoning/spoofing. Double tagging built and verified in Packet Tracer | **4.2 remainder** — rogue DHCP and APs, evil twin, on-path, social engineering, malware. Then 4.3, then a quiz on all of 4.0 |
| **TryHackMe** | **TShark room complete** (2026-09-08). Account made, own workstation rather than the AttackBox — Debian VM on VLAN 50, OpenVPN terminating there | **SOC Fundamentals**, then the two **Nmap** rooms |
| **Network topics** | **Scenario 2 (STP) complete.** Built in its own `stp-lab.pkt` — homelab modelling and exam scenarios stay in separate files now | **Scenario 3 — OSPF, single area** |
| **Packet analysis** | **3 complete** — *First to Last* (FormBook C2), *Easy as 123* (NetSupport RAT), and *Lumma in the Room-ah!* (Lumma infostealer, **all answers correct**) | ***It's a trap!*, 2025-06-13** |
| **Homelab** | **Bastion built** 2026-09-09 — desktop reach narrowed to it, MAC-connect scoped to VLANs 10/20 (the WAN path is closed), NUT verified end to end. **The console is no longer being pursued** — usable blind only, recovery card written | **RA Guard** on the bridge ports, then the **syslog collector** — the prerequisite for everything in Phase 3 |
| **OverTheWire Bandit** | ✅ Complete (mid-2026) | — |

## Block 3 — the network topics queue

**One scenario per entry, each finishable within two blocks.** Topics are drawn from the N10-009 objectives, chosen for things the homelab cannot demonstrate — redundancy, dynamic routing, and failure behaviour need more devices than one switch provides.

**⚠️ This block is exam practice, not homelab modelling.** The Packet Tracer model diverges from the live network in NAT, ACL statefulness, drop-versus-reject behaviour, and syntax. Trying to be both made it confusing and neither. **A RouterOS CHR lab on Proxmox is the tool for pre-flight testing homelab changes** — see the homelab README.

| # | Scenario | Objective | Status |
|---|---|---|---|
| **1** | ~~**NAT and PAT**~~ | 2.1 | **Scrapped 2026-09-09.** Part-built, then abandoned — the 3560 cannot translate, so the build had drifted into modelling a router that is not the homelab's router. Revisit on a device that can do it |
| **2** | **Spanning Tree** | 2.2 | ✅ **Complete 2026-09-09.** Root election, port roles, forced root placement, measured failover, PortFast and BPDU Guard. **Measured: 9 lost pings on PVST+, zero on RSTP** |
| **3** | **OSPF, single area.** Three routers, convergence observed, then a link cut and re-converged | 2.1 | **Next** |
| **4** | **EtherChannel / LACP.** Aggregate two links, verify load distribution, fail one member | 2.2 | Queued |
| **5** | **First-hop redundancy (HSRP).** Two gateways, one virtual address, failover tested from a host | 2.1 | Queued |
| **6** | **DHCP relay.** One central server, several remote VLANs, `ip helper-address`, and the giaddr field read in the capture | 3.4 | Queued |
| **7** | **IPv6 and SLAAC.** Dual-stack a segment, watch RA and DAD, compare with DHCPv6 | 1.7 / 3.4 | Queued |
| **8** | **VLSM and summarisation.** Three sites, one address block, subnet it by hand, then summarise the routes | 1.7 | Queued |
| **9** | **Wireless channel planning.** Three APs, non-overlapping channels, co-channel interference demonstrated | 2.3 | Queued |
| **10** | **QoS.** Voice prioritised over bulk traffic across a congested link | 2.1 | Queued |

**Scenario 2 is deliberately early** — STP has been on the wants list since August and has never been practised.

## Progression triggers

Swap tracks when a condition is met, not on a schedule:

| When | Change |
|---|---|
| **Network+ objectives finish** | Block 1 becomes practice exams (see the ExamCompass order); block 3 moves from Packet Tracer to **Containerlab** |
| **The topics queue empties** | Block 3 becomes Containerlab, or folds into the CHR lab |
| **TryHackMe's useful free rooms run out** | Block 2 becomes CyberDefenders, or HackTheBox once the goal shifts past Security+ |
| **Phase 2 telemetry exists** | Block 5 gains real SOC work — investigating the lab's own logs and alerts, rather than simulated ones |
| **A block in 1-4 is skipped three days running** | Replace it. A track that is being avoided is not being learned. Block 5 is exempt — it is never the one avoided |

## Why TryHackMe rather than HackTheBox

**TryHackMe's free tier is genuinely large — 650+ rooms — and its beginner material is blue-team shaped.** HackTheBox's free offering is narrower and weighted toward offensive work; its defensive content lives in Academy modules that mostly cost money. For a SOC analyst target, TryHackMe is the better free hours.

**⚠️ The SOC Level 1 path is mostly premium.** That is fine for now — the free Pre Security and Cyber Security 101 material overlaps the Network+ syllabus directly, so block 2 reinforces block 1 rather than competing with it. Revisit a subscription when the free network material runs out.

**AttackBox is capped at one hour per day on the free tier**, but many rooms need no AttackBox at all. Prefer those while the cap matters.

**HackTheBox is not dropped, only deferred** — it becomes the better choice after Security+, when the goal shifts from fundamentals to detection engineering and adversary emulation.

## Why the homelab is a block rather than a competitor

It previously competed with these hours and lost, which is the wrong way round. **Simulated SOC work was a rehearsal for the lab; the lab is the thing itself.**

**⚠️ It is also the block that has to wait.** Doing it first feels efficient and is not — see the ordering note at the top. It has no security telemetry yet, so there is nothing to investigate — the switch's logs live in RAM and rotate away within hours. **Building the collection layer is the work**, and it is what makes SOC practice possible later. Start with getting syslog off the switch: everything else builds on top of it.
