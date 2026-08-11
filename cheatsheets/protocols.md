# Ports & Protocols

| Port | Protocol | Description |
|---|---|---|
| 20 | FTP (data) | File transfer, active mode data channel |
| 21 | FTP (control) | File transfer, command channel |
| 22 | SSH | Secure remote CLI, also used by SFTP |
| 23 | Telnet | Plaintext remote CLI (insecure) |
| 25 | SMTP | Sending email between mail servers |
| 53 | DNS | Domain name resolution |
| 67 | DHCP (server) | IP address assignment, server listens here |
| 68 | DHCP (client) | IP address assignment, client listens here |
| 69 | TFTP | Trivial file transfer, UDP, no auth (firmware/boot files) |
| 80 | HTTP | Web traffic (insecure) |
| 110 | POP3 | Retrieving email, typically downloads and removes from server |
| 119 | NNTP | Usenet newsgroups |
| 123 | NTP | Time syncing |
| 135 | RPC | Remote procedure call (check this port to see which high value dynamic port a service is using, then swap to that specific port) |
| 137/138/139 | NetBIOS | Name service/datagram/session (legacy Windows) |
| 143 | IMAP | Retrieving mail, syncs/keeps mail on server |
| 161 | SNMP | Device monitoring/management (agent listens here) |
| 162 | SNMP (trap) | Device sends unsolicited alerts to manager |
| 179 | BGP | Inter-AS routing |
| 389 | LDAP | Directory services queries |

## Review these!

| Port | Protocol | Description |
|---|---|---|
| 443 | HTTPS | Encrypted web traffic (TLS) |
| 445 | SMB | Windows file/printer sharing |
| 465 | SMTPS | SMTP over TLS (implicit) |
| 500 | IKE/ISAKMP | IPsec key exchange (VPN) |
| 514 | Syslog | Centralized logging |
| 587 | SMTP (submission) | Authenticated mail submission from clients |
| 636 | LDAPS | LDAP over TLS |
| 993 | IMAPS | IMAP over TLS |
| 995 | POP3S | POP3 over TLS |
| 1433 | MS SQL | Microsoft SQL Server |
| 1521 | Oracle SQL | Oracle database |
| 1701 | L2TP | VPN tunneling protocol |
| 1723 | PPTP | Older VPN tunneling protocol |
| 3306 | MySQL | MySQL database |
| 3389 | RDP | Windows remote desktop |
| 5060 | SIP | VoIP call signaling, unencrypted |
| 5061 | SIP (TLS) | VoIP call signaling, encrypted |
| 5432 | PostgreSQL | PostgreSQL database |
| 8080 | HTTP (alt) | Common alternate web/proxy port |
