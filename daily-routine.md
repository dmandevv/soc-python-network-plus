# Daily Routine

A guide, not a syllabus. Sources, rankings, and free-tier notes live in **[practice-resources.md](practice-resources.md)** — this file only says **what to work on today and where each track currently stands.**

Claude follows this file to pick up where things left off, and updates *Where things stand* as blocks are completed.

## The shape of a day

**The blocks form a loop, and each day resumes where the previous one stopped.** Do three or four consecutive blocks; whichever you don't reach becomes tomorrow's starting point.

```
  1  Network+  →  2  Packet Tracer  →  3  Packet analysis  →  4  Homelab (2h)
  ↑                                                                        │
  └────────────────────────────────────────────────────────────────────────┘
```

| Block | Track | Source |
|---|---|---|
| **1** | Network+ — one objective section | The walkthrough in `objectives/` |
| **2** | Network configuration | Packet Tracer |
| **3** | Packet analysis | malware-traffic-analysis.net |
| **4** | **Homelab — 2 hours** | The build itself. See [soc-python-homelab](https://github.com/dmandevv/soc-python-homelab) |

**A fixed order means the last block is always the one that gets dropped.** Rotating the start means every track is first roughly one day in four, and none is permanently last.

**⚠️ One asymmetry worth knowing:** Network+ has an exam attached and the others don't. On a short day it is the one to protect — but that is a judgement call, not a rule the rotation enforces.

## Where things stand

**Tomorrow starts at block 4** — today ended after block 3.

| Track | Position | Next |
|---|---|---|
| **Network+** | **17 of 20 — Domain 3 complete** | **4.1 — basic network security concepts** |
| **Packet Tracer** | **Rebuilding the homelab in simulation** — devices cabled, VLANs created, access ports assigned, trunk built and verified on both ends | **Step 4 — SVIs, IP addressing, and `ip routing` on the 3560** |
| **Packet analysis** | **First exercise complete** — *First to Last*, 2026-08-09. FormBook C2, identified the infected host, user account, and C2 destination among decoy traffic | Next exercise **backwards** from 2026-08-09 — the site advises against starting with the oldest, since malware evolves and early exercises are less representative |
| **Homelab** | **Phase 1 complete and verified** — segmented, routed, isolation tested both ways | Console cable test, then restrict `mac-server` to VLAN 10 and add WinNUT. Then **Phase 2** |
| **OverTheWire Bandit** | ✅ Complete (mid-2026) | — |

## Progression triggers

Swap tracks when a condition is met, not on a schedule:

| When | Change |
|---|---|
| **Network+ objectives finish** | Block 1 becomes practice exams; block 2 moves from Packet Tracer to **Containerlab** |
| **Packet Tracer's free courses are done** | Rebuild the homelab's own VLAN design in Cisco syntax, then move to Containerlab |
| **Phase 2 telemetry exists** | Block 4 gains real SOC work — investigating the lab's own logs and alerts, rather than simulated ones |
| **A block is skipped three days running** | Replace it. A track that is being avoided is not being learned |

## Why the homelab is a block rather than a competitor

It previously competed with these hours and lost, which is the wrong way round. **Simulated SOC work was a rehearsal for the lab; the lab is the thing itself.**

**⚠️ It has no security telemetry yet**, so there is nothing to investigate — the switch's logs live in RAM and rotate away within hours. **Building the collection layer is the work**, and it is what makes SOC practice possible later. Start with getting syslog off the switch: everything else builds on top of it.
