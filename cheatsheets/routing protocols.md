# Routing Protocol Types

## Distance-vector
- **Metric:** hop count
- **Shares:** entire routing table, with directly connected neighbors only
- Trusts neighbors' reported distances without knowing actual topology ("routing by rumor")
- **Convergence:** slow, periodic updates/timers, loop-prone (mitigated by split horizon, poison reverse)
- **Example:** RIP (max 15 hops)

## Link-state
- **Metric:** full topology map + Dijkstra's algorithm (shortest path)
- **Shares:** link-state advertisements (own links only), flooded to ALL routers in area/domain
- Every router ends up with the same full topology map, calculates path independently
- **Convergence:** fast, reacts to actual topology change events
- **Examples:** OSPF, IS-IS

## Path-vector
- **Metric:** full AS-path + policy
- **Shares:** route + full path (sequence of ASes it traversed), with neighbors
- **Loop prevention:** reject any route whose AS-path already contains own AS
- **Policy-driven:** AS can prefer/reject routes based on business relationships, not just shortest path
- **Scope:** internet-scale, inter-domain (between ASes)
- **Example:** BGP

## Quick summary table

| Type | Metric basis | Info shared | Scope | Example |
|---|---|---|---|---|
| Distance-vector | Hop count | Full routing table, neighbors only | Small networks | RIP |
| Link-state | Full topology + Dijkstra | Link info, flooded to all routers in domain | Medium-large, intra-domain | OSPF, IS-IS |
| Path-vector | Full AS-path + policy | Route + full path, to neighbors | Internet-scale, inter-domain | BGP |

## EIGRP = hybrid
Cisco proprietary - borrows distance-vector's neighbor exchange model but adds link-state-like fast convergence via DUAL (Diffusing Update Algorithm). Doesn't cleanly fit any single category above.
