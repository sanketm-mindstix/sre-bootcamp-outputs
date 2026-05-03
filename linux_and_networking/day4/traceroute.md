## traceroute command
traceroute is like the “X-ray” version of ping. Instead of just telling you whether a host is reachable, it shows the full path your packets take across the internet—router by router.


### What does traceroute actually do?
traceroute maps the path from your machine to a destination by exploiting: ***Time To Live (TTL)***

#### How it works:
Send packet with TTL = 1
First router reduces TTL → becomes 0 → drops packet
Router sends back ICMP Time Exceeded
Send packet with TTL = 2
Reaches second router → same process
Repeat until destination reached

#### Uses:
ICMP (Linux often)
or UDP (default on many systems)


### Understanding Output

Example:
```bash
traceroute to google.com (142.250.x.x), 30 hops max
 1  192.168.1.1   1.123 ms  1.045 ms  0.987 ms
 2  10.0.0.1      5.321 ms  5.210 ms  5.112 ms
 3  * * *
 4  142.250.x.x  23.456 ms  23.321 ms  23.210 ms
 ```

#### Output Breakdown
| Part          | Meaning                            |
| ------------- | ---------------------------------- |
| `1, 2, 3...`  | Hop number (router position)       |
| IP / Hostname | Router handling packet             |
| `ms values`   | Round-trip time (3 probes per hop) |
| `* * *`       | No response (timeout / blocked)    |

### Core Concepts
1. Hop
Each router between you and destination.

2. Probes
Each hop sends 3 packets by default:
1.123 ms  1.045 ms  0.987 ms

3. Latency per hop
Time taken to reach that router and back.

4. Timeouts (*)
Means:
- Firewall blocked ICMP
- Router ignores requests
- Packet dropped

### Traceroute Flags
| Flag | Full Meaning    | Example Command                 | Output Impact                   | When to Use              |
| ---- | --------------- | ------------------------------- | ------------------------------- | ------------------------ |
| `-m` | Max hops        | `traceroute -m 20 google.com`   | Limits hop count                | Avoid long traces        |
| `-q` | Queries per hop | `traceroute -q 1 google.com`    | Reduces probes (default 3)      | Faster output            |
| `-w` | Wait time       | `traceroute -w 2 google.com`    | Timeout per probe               | Slow networks            |
| `-n` | Numeric output  | `traceroute -n google.com`      | Shows only IPs (no DNS)         | Faster / debug DNS       |
| `-I` | ICMP mode       | `traceroute -I google.com`      | Uses ICMP instead of UDP        | Firewall compatibility   |
| `-T` | TCP mode        | `traceroute -T google.com`      | Uses TCP packets                | Bypass firewalls         |
| `-p` | Port            | `traceroute -p 80 google.com`   | Changes destination port        | Test specific services   |
| `-s` | Source IP       | `traceroute -s <IP> google.com` | Sets source address             | Multi-interface systems  |
| `-i` | Interface       | `traceroute -i eth0 google.com` | Choose network interface        | Multi-network setups     |
| `-f` | First hop       | `traceroute -f 5 google.com`    | Start from hop 5                | Skip initial hops        |
| `-A` | AS lookup       | `traceroute -A google.com`      | Shows Autonomous System numbers | ISP-level debugging      |
| `-e` | Extended output | `traceroute -e google.com`      | More ICMP details               | Deep diagnostics         |
| `-d` | Debug           | `traceroute -d google.com`      | Kernel-level debug info         | Advanced troubleshooting |
