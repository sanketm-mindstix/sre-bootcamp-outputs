## What is Ping?

Your system sends the **ICMP Echo Request packets** to the destinations and waits for a reply

Basically you ask the desination -> 'Are you alive?'
And Destination responed with -> 'Yes, I am'

This is the part of **TCP/IP model**, but ICMP works at the **network level**

### Understanding basic outputs
Example
```bash
PING google.com (142.250.183.14) 56(84) bytes of data.
64 bytes from 142.250.183.14: icmp_seq=1 ttl=117 time=23.4 ms
64 bytes from 142.250.183.14: icmp_seq=2 ttl=117 time=22.8 ms
```

- 64 bytes → size of reply packet
- icmp_seq → sequence number (increments each packet)
- ttl → Time To Live
- time → round-trip time (latency)

### Important Concepts
1. ICMP Sequence (icmp_seq)
Packet number
Helps detect lost packets

2. TTL (Time To Live)
Prevents packets from looping forever
Each router reduces TTL by 1
If TTL = 0 → packet dropped

Typical TTL values:
Linux → 64
Windows → 128

3. Time (Latency)
Measured in milliseconds (ms)

Time taken:
your system → server → your system

Lower = better

4. Packet Loss
Shown at end:

4 packets transmitted, 4 received, 0% packet loss
0% → perfect connection

0% → network issues

5. Round Trip Time Summary
rtt min/avg/max/mdev = 22.8/23.1/23.4/0.2 ms
min → fastest response
avg → average latency
max → slowest response
mdev → variation (jitter)


### Common Flags
| Flag | Full Meaning        | Example Command           | What It Does                             | When to Use                                   |
| ---- | ------------------- | ------------------------- | ---------------------------------------- | --------------------------------------------- |
| `-c` | Count               | `ping -c 4 google.com`    | Sends fixed number of packets            | Quick connectivity test without infinite ping |
| `-i` | Interval            | `ping -i 2 google.com`    | Sets delay between packets (seconds)     | Reduce network load or test slow intervals    |
| `-s` | Packet Size         | `ping -s 1000 google.com` | Changes packet payload size              | Test MTU / network performance                |
| `-t` | TTL (Time To Live)  | `ping -t 50 google.com`   | Sets TTL value manually                  | Debug routing / hop limits                    |
| `-W` | Timeout             | `ping -W 2 google.com`    | Wait time for each reply (seconds)       | Detect slow/unresponsive hosts                |
| `-w` | Deadline            | `ping -w 10 google.com`   | Total time before ping stops             | Time-bound monitoring                         |
| `-f` | Flood               | `ping -f google.com`      | Sends packets rapidly (no delay)         | Stress testing (⚠️ root required)             |
| `-a` | Audible             | `ping -a google.com`      | Beep on each reply                       | Monitoring with sound alerts                  |
| `-q` | Quiet               | `ping -c 5 -q google.com` | Only summary output                      | Clean logs / scripting                        |
| `-v` | Verbose             | `ping -v google.com`      | Detailed debugging output                | Deep troubleshooting                          |
| `-n` | Numeric             | `ping -n google.com`      | Skip DNS resolution                      | Faster output / debug DNS issues              |
| `-4` | IPv4                | `ping -4 google.com`      | Force IPv4                               | When dual-stack causes issues                 |
| `-6` | IPv6                | `ping -6 google.com`      | Force IPv6                               | Test IPv6 connectivity                        |
| `-l` | Preload             | `ping -l 5 google.com`    | Send multiple packets instantly at start | Burst testing                                 |
| `-D` | Timestamp           | `ping -D google.com`      | Adds timestamp in output                 | Log analysis / debugging delays               |
| `-O` | Report lost packets | `ping -O google.com`      | Shows lost packets before next reply     | Detect intermittent drops                     |
