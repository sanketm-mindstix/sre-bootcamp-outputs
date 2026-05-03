## nslookup Command

What IP (or DNS info) is associated with this domain?

### Basic Output Explained
```bash
Server:  192.168.31.1
Address: 192.168.31.1#53

Non-authoritative answer:
Name:    google.com
Address: 142.250.183.14
```

#### Breakdown
| Line                       | Meaning                                  |
| -------------------------- | ---------------------------------------- |
| `Server`                   | DNS server used (your router/ISP)        |
| `Address`                  | DNS server IP + port 53                  |
| `Non-authoritative answer` | Response is cached (not original source) |
| `Name`                     | Domain queried                           |
| `Address`                  | Resolved IP                              |


### Important Concepts

#### Authoritative vs Non-authoritative
| Type              | Meaning                         |
| ----------------- | ------------------------------- |
| Authoritative     | Direct from domain’s DNS server |
| Non-authoritative | From cache (ISP/local DNS)      |

### Common Flags
| Flag / Usage      | Meaning            | Example                               | Output Impact               | When to Use            |
| ----------------- | ------------------ | ------------------------------------- | --------------------------- | ---------------------- |
| `nslookup domain` | Basic lookup       | `nslookup google.com`                 | Shows A record              | Quick IP check         |
| `-type=A`         | IPv4 record        | `nslookup -type=A google.com`         | Shows IPv4 only             | Default check          |
| `-type=AAAA`      | IPv6 record        | `nslookup -type=AAAA google.com`      | Shows IPv6                  | IPv6 debugging         |
| `-type=MX`        | Mail servers       | `nslookup -type=MX gmail.com`         | Shows mail servers          | Email setup/debug      |
| `-type=NS`        | Name servers       | `nslookup -type=NS google.com`        | Shows DNS servers           | DNS infra check        |
| `-type=CNAME`     | Alias record       | `nslookup -type=CNAME www.google.com` | Shows alias                 | CDN/debugging          |
| `-type=TXT`       | Text records       | `nslookup -type=TXT google.com`       | Shows TXT entries           | SPF/DKIM verification  |
| `-type=SOA`       | Start of authority | `nslookup -type=SOA google.com`       | Shows domain authority info | Advanced DNS debugging |
| `server <DNS>`    | Use specific DNS   | `nslookup google.com 8.8.8.8`         | Uses Google DNS             | Compare DNS results    |
| `-debug`          | Verbose output     | `nslookup -debug google.com`          | Full DNS query details      | Deep debugging         |
| `-timeout=<sec>`  | Query timeout      | `nslookup -timeout=2 google.com`      | Faster fail                 | Slow networks          |
| `-port=<num>`     | Custom DNS port    | `nslookup -port=5353 google.com`      | Uses custom port            | Special setups         |
| `-retry=<num>`    | Retry attempts     | `nslookup -retry=1 google.com`        | Fewer retries               | Faster response        |


