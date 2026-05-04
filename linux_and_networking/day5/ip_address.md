## IP Address

IPv4 is a 32-bit logical address used to uniquely identify a device on a network.
Example
192.168.1.180


### Reserved IP Ranges
#### Private IP Ranges
These cannot be routed on internet
These Private ranges were defined in RFC 1918
They were inspired by classful structure, but:
They are now used with CIDR

| Range                         | CIDR | Use                                 |
| ----------------------------- | ---- | ----------------------------------- |
| 10.0.0.0 – 10.255.255.255     | /8   | Large private networks (cloud VPCs) |
| 172.16.0.0 – 172.31.255.255   | /12  | Medium private networks             |
| 192.168.0.0 – 192.168.255.255 | /16  | Home/office networks                |

#### Special Reserved IP Addresses
| Range           | Purpose                       |
| --------------- | ----------------------------- |
| 127.0.0.0/8     | Loopback (localhost)          |
| 169.254.0.0/16  | APIPA (auto IP if DHCP fails) |
| 0.0.0.0         | “This host” / default route   |
| 255.255.255.255 | Broadcast                     |

### Private vs Public
#### Private IP
Used inside the local network and is not visible on internet

#### Public IP
- Assigned by ISP/cloud
- Globally unique

### NAT (Network Address Translation)
NAT allows multiple devices with private IPs to share a single public IP.

#### How it works:
Device sends request:
192.168.1.10 → Google

Router replaces source IP:
192.168.1.10 → 49.x.x.x (public IP)

Router keeps mapping table
Response comes back → router forwards to correct device

NAT is required because Private IPs are not routable on internet


### Add Default Gateway Concept
The router IP address used by a device to communicate outside its subnet.

So, most commonly, Default Gateway is the first or last usable host IP from the subnet. (Can be any usable host IP)

Example:
IP: 192.168.1.10
Gateway: 192.168.1.1

So basically 
#### 1. Network Address
The first IP address of a subnet that uniquely identifies the network itself. It is not assignable to any device.

#### 2. Broadcast Address
The last IP address of a subnet used to send data to all devices within that subnet. It is not assignable to any device.

#### 3. Default Gateway
A router’s IP address within a subnet that devices use to communicate with networks outside their own subnet.


### CIDR (Classless Inter Domain Routing)
CIDR is a way to represent: IP Address + how much of it is network
Example: 192.168.1.0/24

/24 means:
First 24 bits = network
Remaining 8 bits = hosts

#### Why CIDR Exists
Earlier (old system), networks were fixed:
| Class | Range                 | Default Mask  | CIDR Equivalent |
| ----- | --------------------- | ------------- | --------------- |
| A     | 1.0.0.0 – 126.x.x.x   | 255.0.0.0     | /8              |
| B     | 128.0.0.0 – 191.x.x.x | 255.255.0.0   | /16             |
| C     | 192.0.0.0 – 223.x.x.x | 255.255.255.0 | /24             |


So first few bits of IP decided the class
| Class | First Bits | Example     |
| ----- | ---------- | ----------- |
| A     | 0xxxxxxx   | 10.0.0.1    |
| B     | 10xxxxxx   | 172.16.0.1  |
| C     | 110xxxxx   | 192.168.1.1 |

Problem with Classful System
1. Massive IP Wastage

Example:
A company needs 300 IPs

Options:
Class C → 254 IPs (not enough)
Class B → 65,534 IPs (too many)

Results in Huge wastage of IP addresses

2. Routing Table Explosion
Routers had to maintain huge routing tables because:
Networks weren’t grouped efficiently

##### CIDR solved this by allowing any subnet size

CIDR Table 
| CIDR | Subnet Mask     | Total IPs | Usable |
| ---- | --------------- | --------- | ------ |
| /32  | 255.255.255.255 | 1         | 1      |
| /30  | 255.255.255.252 | 4         | 2      |
| /28  | 255.255.255.240 | 16        | 14     |
| /24  | 255.255.255.0   | 256       | 254    |
| /16  | 255.255.0.0     | 65,536    | 65,534 |
| /8   | 255.0.0.0       | 16M+      | ~16M   |

1. Flexible Network Sizes

Now you can create exact-sized networks

Example:
Need ~500 IPs → use /23 (512 IPs)

No more waste like Class B


2. Efficient IP Allocation

Instead of giving:
One big Class B network

We can give:
Multiple smaller subnets


3. Route Aggregation (Super Important)

CIDR allows summarization

Instead of 4 routes:
192.168.0.0/24
192.168.1.0/24
192.168.2.0/24
192.168.3.0/24

You can write:
192.168.0.0/22

- Fewer routing entries
- Faster routing



### Subnetting
An IPv4 address (e.g. 192.168.1.0) has two logical parts:

Network part → identifies the network
Host part → identifies a device inside that network

The subnet mask tells us which bits belong to network vs host.
Example - 255.255.255.0

Now the machines don't these numbers. They understand the binary numbers i.e 0s and 1s

So, if we convert the IP address to the binary form, it becomes
| 192      | 168      | 1        | 0        |
|----------|----------|----------|----------|
| 11000000 | 10101000 | 00000001 | 00000000 |
|----------|----------|----------|----------|
|----------|----------|----------|----------|
| Sunet Mask |        |          |          |
|----------|----------|----------|----------|
| 255      | 255      | 255      | 0        |
|----------|----------|----------|----------|
| 11111111 | 11111111 | 11111111 | 00000000 |

The parts of the Binary IP which are inline with the 1s in the Binary Subnet Mask is the Network Address

So, in this example the the first 3 octet are the network Address and the last octet is the Host address


- Example 1:
IP: 192.168.1.130
Mask: 255.255.255.128 (i.e. /25) 

| Octet | IP Binary | Mask Binary |
| ----- | --------- | ----------- |
| 4th   | 10000010  | 10000000    |

| Type    | Bits          |
| ------- | ------------- |
| Network | first 25 bits |
| Host    | last 7 bits   |

Result
Network: 192.168.1.128
Broadcast: 192.168.1.255
Host Range: 192.168.1.129 – 192.168.1.254

- Example 2:
IP: 10.0.5.23

Mask: 255.255.255.240 (/28)

| Octet | IP Binary | Mask Binary |
| ----- | --------- | ----------- |
| 4th   | 00010111  | 11110000    |


Result
Network: 10.0.5.16
Broadcast: 10.0.5.31
Usable: 10.0.5.17 – 10.0.5.30

#### Rule for Valid Subnet Mask

A valid subnet mask must have:

All 1s first → then all 0s
NO mixing

Valid examples:
```bash
11111111
11110000
11111100
```
Invalid:
```bash
11100001
10101010
```

Valid Octets
| Decimal | Binary   |
| ------- | -------- |
| 0       | 00000000 |
| 128     | 10000000 |
| 192     | 11000000 |
| 224     | 11100000 |
| 240     | 11110000 |
| 248     | 11111000 |
| 252     | 11111100 |
| 254     | 11111110 |
| 255     | 11111111 |

### Why Subnet?
So the networks can be logiclly broken down into the smaller networks

### Example - Create Subnets for the small IT Firm with around 200 employees
| Department  | Users |
| ----------- | ----- |
| Engineering | 100   |
| Sales       | 40    |
| HR          | 20    |
| Finance     | 20    |

Let's start with a Private Network
10.0.0.0/24 -> 254 Usable Hosts

Allocate Subnets
| Department  | Subnet | Hosts |
| ----------- | ------ | ----- |
| Engineering | /25    | 126   |
| Sales       | /26    | 62    |
| HR          | /27    | 30    |
| Finance     | /27    | 30    |

Assign Subnets
1. Engineering
10.0.0.0/25
Range: 10.0.0.1 – 10.0.0.126
Broadcast: 10.0.0.127

2. Sales
10.0.0.128/26
Range: 10.0.0.129 – 10.0.0.190
Broadcast: 10.0.0.191

3. HR
10.0.0.192/27
Range: 10.0.0.193 – 10.0.0.222
Broadcast: 10.0.0.223

4. Finance
10.0.0.224/27
Range: 10.0.0.225 – 10.0.0.254
Broadcast: 10.0.0.255