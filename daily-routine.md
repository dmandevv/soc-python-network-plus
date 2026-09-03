# Daily Routine

A guide, not a syllabus. Sources, rankings, and free-tier notes live in **[practice-resources.md](practice-resources.md)** — this file only says **what to work on today and where each track currently stands.**

Claude follows this file to pick up where things left off, and updates *Where things stand* as blocks are completed.

## The shape of a day

| Block | Track | Source |
|---|---|---|
| **1** | **Network+ — one objective section** | The objectives walkthrough in `objectives/` |
| **2** | **Network configuration** | Packet Tracer |
| **3** | **Packet analysis** | malware-traffic-analysis.net |
| **4** | **SOC simulation** | LetsDefend |
| *5 — optional* | *Whatever has momentum* | *TryHackMe, CyberDefenders, or picoCTF* |

**Block 1 first, while attention is freshest** — it is the one with an exam attached.

**Blocks 2–4 can be reordered freely.** Skipping one is fine; skipping the same one repeatedly means it should be swapped for something from the reserve list in practice-resources.md.

## Where things stand

| Track | Position | Next |
|---|---|---|
| **Network+** | 16 of 20 objectives complete | **3.5 — network access and management methods** |
| **Packet Tracer** | Not started | Install, then Networking Academy *Networking Basics* |
| **Packet analysis** | Not started | Oldest exercise on malware-traffic-analysis.net, working forward |
| **LetsDefend** | Not started | *SOC Fundamentals* |
| **OverTheWire Bandit** | ✅ Complete (mid-2026) | — |

## Progression triggers

Swap tracks when a condition is met, not on a schedule:

| When | Change |
|---|---|
| **Network+ objectives finish** | Block 1 becomes practice exams; block 2 moves from Packet Tracer to **Containerlab** |
| **Packet Tracer's free courses are done** | Rebuild the homelab's own VLAN design in Cisco syntax, then move to Containerlab |
| **Phase 3 begins** | Block 4 moves from LetsDefend to the **live SOC** — real alerts beat simulated ones |
| **A block is skipped three days running** | Replace it. A track that is being avoided is not being learned |

## ⚠️ The lab competes for these hours

Homelab Phase 2 is hands-on work these platforms partly substitute for. **When both are available, prefer the lab** — LetsDefend simulates investigating alerts, while the network generates real ones.
