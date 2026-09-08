# Analysis Lessons

Tradecraft from the packet analysis and SOC practice track — **how to reason**, not what things are. Facts belong in `objectives/`.

---

## Derived is not confirmed, and a neat derivation deserves more scepticism

**2026-09-04 — malware-traffic-analysis.net, "Easy as 123"**

The capture contained two hosts. One had the hostname **`brads-MBP`**; the other, the infected machine, had a user account **`brolf`**. Both read plausibly as "Brad", so the full name was inferred as **Brad Rolf**.

**The answer was Becka Rolf.** The exercise had deliberately planted a second host with a decoy name.

**Three errors, stacked:**

1. **Name similarity was treated as evidence.** `b` plus a surname rules out almost nothing — Brad, Becka, Ben, Bruno all fit.
2. **Fields were correlated across two different hosts** without confirming they belonged together.
3. **The inference stopped the search.** Once the answer felt settled, the filter that would have disproved it never got run.

**The filter that would have caught it:**

```
frame matches "(?i)rolf"
```

**Search the unambiguous half.** The surname is searchable; the first initial was already a guess. A display name containing "Rolf" would have surfaced the real value in one filter.

**The generalisable form: an inference that fits neatly is the most dangerous kind, because it feels like an answer and ends the investigation.** Label derivations as derived — then go and confirm them anyway.

---

## Verify correlation before combining fields

**Same exercise.** A hostname from DHCP and a MAC vendor from another packet were about to be reported as one host. **The client MAC in the DHCP Discover was Realtek; the MAC under investigation was Intel — two different machines.**

**Thirty seconds of checking prevented a report naming the wrong device.** Attribute by MAC rather than IP where possible: `eth.addr == ...` survives address changes.

---

## A first-packet timeout is usually ARP, not a fault

Cross-VLAN pings frequently lose the first packet while ARP resolves on both sides of the routing hop. **Never diagnose from a single ping** — send three, and treat a lone timeout followed by success as normal.

---

## Knowing when the question is answered

**The exercise asked which host was infected.** Three independent indicators — C2 beaconing, SMB to the domain controller's `IPC$`, and an `AutoRun.inf` write attempt — settled it well before the RPC traffic was understood.

**Continuing to dig past a sufficient answer is a real failure mode**, and recognising the stopping point is a skill in itself. The deeper analysis remains available if a later question needs it.

---

## Write the claim you can defend

> Lateral movement toward the domain controller: SMB2 connection to `IPC$` and an attempted `AutoRun.inf` write. **Execution on the DC not confirmed from this capture.**

rather than

> Tried to execute code on the domain controller.

**The second overstates the evidence.** The distinction between observed and inferred is what makes a report survive scrutiny.

## Corroboration works — *Lumma in the Room-ah!*, completed 2026-09-07

**All answers correct**, and the method is worth recording because it was the direct fix for the previous exercise's failure.

The account name was found once, and then **deliberately not written down** until it had been checked three ways: the account string and the full name appearing together in a single LDAP `searchResEntry` rather than being joined by inference, the name tied to the **infected host's IP** rather than merely present somewhere in the capture, and a count of how many non-machine accounts existed at all (`kerberos.CNameString && !(kerberos.CNameString contains "$")`).

**The second check is the one that would have caught the Becka Rolf error.** That mistake was never about reading the wrong field — `brolf` was correct. It was about joining an artifact from one host to an artifact from another because the story fit. Filtering the corroborating search by the infected host's address makes that specific error impossible to commit silently.

**⚠️ The habit to keep: one artifact is a hypothesis.** Finding a name that matches is the moment to slow down, not the moment to finish.
