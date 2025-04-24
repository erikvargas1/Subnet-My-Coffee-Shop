# You-Suck-at-Subnetting

The IETF (Internet Engineering Task Force) introduced **CIDR** in 1993 to replace the "Classful" addressing system. With CIDR the classful requirments of: `Class A = /24, Class B = /16, Class C = /24` were removed. 

**CIDR allows for larger networks to be split into smaller networks**, allowing for greater efficiency. CIDR allows us to assign different prefix lengths `EX: /21 instead of /24 for a Class C.`

These smaller networks are called "subnetworks" or "subnets".

RFC 1918 Private Addresses. These private Addresses are not publicly routable on the internet. NAT fixes this issue

A | 10.0.0.0 - 10.255.255.255

B | 172.16.0.0 - 172.31.255.255

C | 192.168.0.0 - 192.168.255.255

------------
## Binary to Decimal Conversion

11000000.10101000.00000001.00010101 = 192.168.1.21

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-----|----|----|----|---|---|---|---|
|  1  | 0  | 1  | 0  | 1 | 0 | 0 | 0 |

128+32+8= 168

--------------
## Decimal to Binary Conversion
172.16.34.3

10101100.00010000.00100010.00000011

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
 
------
## let’s subnet your home network
NOTE: when we need more networks we borrow host bits.

**Your Home Network: 192.168.1.0/24**

**Question: We need to create 4 networks** 

11000000.10101000.00000001.00000000 = 192.168.1.0
11111111.11111111.11111111.00000000 = 255.255.255.0 = /24


| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-----|----|----|----|---|---|---|---|
| 256 | 128| 64 | 32 | 16| 8 | 4 | 2 |

1) Use the chart to calculate how many host bits you need to hack to create 4 networks
 - hack 2 bits to create 4 networks.

2) Hack the host bits
11111111.11111111.11111111.00000000 = 255.255.255.0 = /24
New subnet mask
11111111.11111111.11111111.11|000000 = 255.255.255.192 = /26

3) Find the increment
   1     1   0     0   0   0  0    0    = 192 
| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

The increment is 64. By using the last hacked increment we can determine the size of our networks and what the ranges are.

4) Create your /26 networks (remember to -1)
192.168.1.0 - 192.168.1.63
192.168.1.64 - 192.168.1.127
192.168.1.128 - 192.168.1.191
192.168.1.192 - 192.168.1.255

5) How many hosts are in each of these networks?
11111111.11111111.11111111.11|000000 = 255.255.255.192 = /26
   
  1      1   0    0   0    0   0   0
  
| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-----|----|----|----|---|---|---|---|
| 256 | 128| 64 | 32 | 16| 8 | 4 | 2 |


By using the chart and counting the number of hosts bits. We can determine the # number of host for each network 
64 total hosts and 62 usable hosts addresses.

-------------------------------------






