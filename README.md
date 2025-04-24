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



