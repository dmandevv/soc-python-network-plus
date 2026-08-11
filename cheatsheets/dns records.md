# DNS Records

| Record | Full name | Function |
|---|---|---|
| A | Address | Maps a domain name to an IPv4 address |
| AAAA | Quad A | Maps a domain name to an IPv6 address |
| CNAME | Canonical Name | Creates an alias pointing one domain name to another |
| MX | Mail Exchange | Maps a domain to its mail servers (tells others where to send your mail to) |
| NS | Name Server | Authoritative name servers for the domain |
| PTR | Pointer | Reverse lookup - maps an IP address to a domain name |
| SOA | Start of Authority | Zone's administrative info (primary NS, admin contact, serial number, timers, TTL) |
| SRV | Service | Specifies host/port for a service (e.g. SIP server) |
| TXT | Text | Arbitrary text data - used for SPF, DKIM, domain verification |
| CAA | Certification Authority Authorization | Specifies which Certificate Authorities are permitted to issue SSL/TLS certificates for the domain |
| NAPTR | Naming Authority Pointer | Used in some VoIP/SIP service discovery scenarios |

## TXT-based email security records
(these live *inside* TXT records, not as their own record type)

- **SPF** - authorized mail servers for domain (who can send mail from this domain)
- **DKIM** - email signing verification
- **DMARC** - email authentication policy
