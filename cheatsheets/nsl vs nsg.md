# Network Security List (NSL) vs Network Security Group (NSG)

Both are cloud-native, firewall-like rule sets for controlling inbound/outbound traffic in cloud computing environments — the difference is scope/granularity.

| | NSL (Network Security List) | NSG (Network Security Group) |
|---|---|---|
| **Scope** | Subnet level | Specific virtual NICs |
| **Granularity** | Less granular (applies to everything in the subnet) | More granular (applies per resource/interface) |
| **Provider** | Oracle Cloud Infrastructure (OCI) term | Microsoft Azure term (also used generically) |

## Shared characteristics
- Provides firewall-like capabilities
- Used for controlling inbound and outbound traffic in cloud computing environments
- Rule-based (permit/deny by IP/port/protocol) — NOT intrusion detection/prevention (that's IDS/IPS)
- Both are cloud/virtualized-environment constructs, not traditional/non-virtualized networking

## Cross-provider equivalents

| Provider | Subnet-level (broad) | Resource-level (granular) |
|---|---|---|
| AWS | Network ACL (stateless) | Security Group (stateful) |
| Azure | NSG (one construct, applied at subnet or NIC level) | NSG (same construct) |
| OCI (Oracle Cloud) | Security List (NSL) | Network Security Group (NSG) |

**Key exam trap:** Azure uses one construct (NSG) flexibly at either scope. AWS and OCI split it into two separate constructs — a broader subnet-level list/ACL and a more granular per-resource security group.
