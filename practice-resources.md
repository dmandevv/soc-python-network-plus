# Hands-On Practice Resources

Free, hands-on training to run alongside the Network+ objectives walkthrough. Ranked for **doing** rather than reading, and chosen to **complement the homelab rather than duplicate it**.

**Verification note:** free tiers change often. Entries marked ✅ were confirmed on 2026-09-01; the rest come from prior knowledge and are worth checking before committing time.

## ⚠️ The best lab is the one already owned

A managed switch, a hypervisor, and a live internet-facing service is more than most learners have. **These resources should fill the gaps that lab cannot** — other vendors' CLIs, real attack traffic, forensic artifacts, and adversary behaviour better not generated at home. Where a platform duplicates something the CRS326 can do, prefer the CRS326.

## Working set

| # | Source | What you do | Free scope | Why ranked here |
|---|---|---|---|---|
| **1** | **Cisco Packet Tracer** + Networking Academy | Build topologies, configure routers and switches, break and repair them | **Fully free** with a free account | Closest to the exam's mental model, and fills the lab's one real gap — **Cisco CLI**, which Network+ and most employers assume |
| **2** | **malware-traffic-analysis.net** | Analyse **real packet captures from real infections**, with answer keys | **Free, no account** | The best free packet-analysis practice available. Bridges Network+ protocol knowledge and SOC detection in a single exercise |
| **3** | **TryHackMe** — free rooms | Browser-based hands-on labs | ✅ Free rooms only; **AttackBox limited to 1 hr/day** | Large free catalogue, and many rooms need no AttackBox. Start with *Pre Security* and *Cyber Security 101* |
| **4** | **LetsDefend** — Basic plan | **Alerts arrive in a queue; you investigate, escalate, and close them** | ✅ Free tier confirmed; free courses include SOC Fundamentals, Phishing Email Analysis, Detecting Web Attacks, Network Fundamentals | The closest free simulation of actual Tier 1 analyst work |
| **5** | ~~**OverTheWire — Bandit**~~ | 30+ levels of Linux command line over SSH | **Entirely free** | ✅ **Already completed (mid-2026).** Listed because it is the prerequisite everything downstream assumes — revisit only if the CLI ever feels like the obstacle |
| **6** | **CyberDefenders** | Blue team challenges using **real captures, memory images, and logs** | ✅ Mix of free and premium | DFIR practice with genuine artifacts — Wireshark, Volatility, KQL |
| **7** | **Splunk Free + Boss of the SOC datasets** | Stand up a SIEM, ingest the BOTS data, hunt through it | **Free licence, 500 MB/day**; datasets free | Self-hosted on the Dell. **Direct rehearsal for Phase 3** |
| **8** | **Containerlab** | Define multi-vendor topologies as code and run them in containers | **Free, open source** | Modern network labbing with FRR and Arista cEOS. Runs on hardware already owned |
| **9** | **Juniper Open Learning** | Courses with labs, **plus free JNCIA exam vouchers** | **Free** | Badly underused. A second vendor's CLI is genuinely clarifying about what is standard and what is Cisco convention |
| **10** | **picoCTF** | Permanently available beginner CTF | **Entirely free** | Networking and forensics categories, useful on days that want a puzzle rather than a syllabus |

## Also worth knowing

| Source | What it offers | Free scope |
|---|---|---|
| **GNS3 / EVE-NG Community** | Traditional emulators running real vendor images | Free; images sourced separately |
| **Blue Team Labs Online** | Investigation challenges | Free tier exists — scope unverified |
| **HTB Academy** | Structured modules | Some free; most consume paid "cubes" |
| **Microsoft Learn + Azure free tier** | **KQL and Sentinel** practice with sandboxes | Free learning paths |
| **Wireshark sample captures** | Official capture library | Free — pairs with resource 2 |
| **RangeForce Free Edition** | Hands-on cyber range modules | Exists; scope unverified and recently changed |
| **Antisyphon** | Live courses, pay-what-you-can | Some genuinely free |
| **Open Security Training** | Deep free courses | Free; older material, still sound |
| **Security Onion / Wazuh documentation** | Building the stack | Free — **and it is Phase 3 itself** |

## ⚠️ On volume

**Three paths run consistently beat four run sporadically.** The failure mode is breadth without retention — touching six platforms and becoming competent at none. The homelab also competes for the same hours, and Phase 2 is hands-on work these platforms partly substitute for.

## Rotation

Bandit being already complete removes the three-week ramp — packet analysis starts immediately.

| Block | Now | After the Network+ objectives finish |
|---|---|---|
| **1** | **Network+ objective section** | Practice exams |
| **2** | **Packet Tracer** | **Containerlab** |
| **3** | **malware-traffic-analysis.net** | unchanged |
| **4** | **LetsDefend** | **Splunk + BOTS**, then the live Phase 3 SOC |
| *5* | *optional — TryHackMe, CyberDefenders, picoCTF* | *unchanged* |

**Packet Tracer belongs to the Network+ period and Containerlab to what follows** — the first reinforces the exam, the second builds past it.

Day-to-day position is tracked in **[daily-routine.md](daily-routine.md)**.
