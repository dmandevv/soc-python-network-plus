# Daily Routine

A guide, not a syllabus. Sources, rankings, and free-tier notes live in **[practice-resources.md](practice-resources.md)** — this file only says **what to work on today and where each track currently stands.**

Claude follows this file to pick up where things left off, and updates *Where things stand* as blocks are completed.

## The shape of a day

**Every day starts at block 1 and works down the list in order.** No rotation.

```
  1  Network+  →  2  TryHackMe  →  3  Network topics  →  4  Packet analysis  →  5  Homelab (2h)
```

| Block | Track | Source |
|---|---|---|
| **1** | Network+ — one objective section | The walkthrough in `objectives/` |
| **2** | **TryHackMe** — free rooms | [tryhackme.com](https://tryhackme.com) |
| **3** | **Network topics** — one scenario, built and verified | Packet Tracer. Queue below |
| **4** | Packet analysis | malware-traffic-analysis.net |
| **5** | **Homelab — 2 hours** | The build itself. See [soc-python-homelab](https://github.com/dmandevv/soc-python-homelab) |

**The order is deliberate, and the reason is motivational rather than technical.** The homelab is the part that needs no discipline — it would happily consume a whole day on its own. Everything above it is necessary and comparatively dull. **Putting the lab last makes it the thing the other four blocks are paid for**, which is the only arrangement where the studying reliably happens.

**⚠️ So the failure mode to watch is the opposite of what a fixed order usually risks.** Block 5 will not get skipped. The danger is block 5 starting at 10am — the homelab quietly annexing the morning, and blocks 1-4 becoming something that happens tomorrow.

Two guards, both worth keeping:
- **The lab does not open until blocks 1-4 are done.** Not a rule about effort, just about order. Short blocks are fine; skipped ones are not.
- **The three-day skip trigger applies to blocks 1-4 only.** If one of them goes three days untouched, it gets replaced — the homelab is not a candidate for that trigger, because avoidance is not its problem.

## Where things stand

| Track | Position | Next |
|---|---|---|
| **Network+** | **17 of 20 — 4.1 half complete.** Logical security through physical security written and quizzed (20/20) | **4.1 remainder** — deception technologies, security terminology, audits and compliance, segmentation enforcement. Then 4.2, then a quiz on all of 4.0 |
| **TryHackMe** | **Account not yet made.** The workstation it runs on is built: Debian VM at `10.10.50.10` on the new sandbox VLAN, isolated and verified. No tooling installed yet | **Install tshark and OpenVPN**, make a free account, download the `.ovpn` config, connect, then start the **TShark** room |
| **Network topics** | **Scenario 1 part-built.** XB6 router and Internet-Host placed; the 3560's `Fa0/1` is a routed port on `10.0.0.2`. **NAT cannot run on the 3560** — verified by `ip ?` — so translation moves to XB6 | **Finish scenario 1** (NAT/PAT on XB6), then **scenario 2 — STP** |
| **Packet analysis** | **3 complete** — *First to Last* (FormBook C2), *Easy as 123* (NetSupport RAT), and *Lumma in the Room-ah!* (Lumma infostealer, **all answers correct**) | ***It's a trap!*, 2025-06-13** |
| **Homelab** | **Phase 1 complete.** VLAN 50 sandbox added 2026-09-07 — segment, gateway, DHCP, firewall policy, and a Debian VM, isolation verified both ways | Console cable test when the replacement arrives, then restrict `mac-server` to VLAN 10, **restrict `/ip neighbor discovery-settings` to exclude `vlan50`**, and add WinNUT. Then **Phase 2** |
| **OverTheWire Bandit** | ✅ Complete (mid-2026) | — |

## Block 3 — the network topics queue

**One scenario per entry, each finishable within two blocks.** Topics are drawn from the N10-009 objectives, chosen for things the homelab cannot demonstrate — redundancy, dynamic routing, and failure behaviour need more devices than one switch provides.

**⚠️ This block is exam practice, not homelab modelling.** The Packet Tracer model diverges from the live network in NAT, ACL statefulness, drop-versus-reject behaviour, and syntax. Trying to be both made it confusing and neither. **A RouterOS CHR lab on Proxmox is the tool for pre-flight testing homelab changes** — see the homelab README.

| # | Scenario | Objective | Status |
|---|---|---|---|
| **1** | **NAT and PAT.** Private VLANs translated to one outside address; prove it by reading the source address in the packet at the far end | 2.1 | **In progress** |
| **2** | **Spanning Tree.** Three switches, redundant links. Watch the root election, identify port roles, then force root placement and watch it change | 2.2 | Queued |
| **3** | **OSPF, single area.** Three routers, convergence observed, then a link cut and re-converged | 2.1 | Queued |
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
