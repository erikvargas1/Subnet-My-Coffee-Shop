# Subnet-My-Coffee-Shop
---------
## IPV4 Classful Addresssing

| **Address Class** | **Range**                         | **Default Subnet Mask**     |
|-------------------|-----------------------------------|------------------------------|
| **A**             | 1.0.0.0 to 127.255.255.255        | 255.0.0.0                    |
| **B**             | 128.0.0.0 to 191.255.255.255      | 255.255.0.0                  |
| **C**             | 192.0.0.0 to 223.255.255.255      | 255.255.255.0                |
| **D**             | 224.0.0.0 to 239.255.255.255      | Reserved for Multicasting    |
| **E**             | 240.0.0.0 to 254.255.255.255      | Experimental                 |

> **Note:** Class A addresses `127.0.0.0 to 127.255.255.255` cannot be used and are reserved for **loopback testing**.
-------

The IETF (Internet Engineering Task Force) introduced **CIDR** in 1993 to replace the "Classful" addressing system. With CIDR the classful requirments of: `Class A = /24, Class B = /16, Class C = /24` were removed. 

**CIDR allows for larger networks to be split into smaller networks**, allowing for greater efficiency. CIDR allows us to assign different prefix lengths `EX: /21 instead of /24 for a Class C.`

These smaller networks are called "subnetworks" or "subnets".

RFC 1918 Private Addresses. These private Addresses are not publicly routable on the internet. NAT fixes this issue

A | 10.0.0.0 - 10.255.255.255

B | 172.16.0.0 - 172.31.255.255

C | 192.168.0.0 - 192.168.255.255

------------
## Binary to Decimal Conversion

11000000.|10101000.|00000001.|00010101 = 192.168.1.21

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-----|----|----|----|---|---|---|---|
|  1  | 0  | 1  | 0  | 1 | 0 | 0 | 0 |

128+32+8= 168

--------------
## Decimal to Binary Conversion
172.16.34.3

10101100.|00010000.|00100010.|00000011

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
 
------
# 🏠 Let’s Subnet Your Home Network

> **Note:** When we need more networks, we borrow **host bits**.

---

## Your Home Network

```
Network Address: 192.168.1.0/24
Binary:          11000000.10101000.00000001.00000000

Subnet Mask:     255.255.255.0 (/24)
Binary:          11111111.11111111.11111111.00000000
```


## Question: We Need to Create 4 Networks

Step 1: Use the Nosferatz chart to calculate how many host bits we need to hack to create 4 networks

```
          0     0    |  0    0    0    0     1    1
``` 
|  Bit  | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-------|-----|----|----|----|---|---|---|---|
| Value | 256 |128 | 64 | 32 |16 | 8 | 4 | 2 |


✅ To create **4 networks**, we need to **hack 2 host bits**. 

-----------

### Step 2: Hack the Host Bits

Original Subnet Mask (Binary):  
```
11111111.11111111.11111111.00000000 = 255.255.255.0 (/24)
```

New Subnet Mask After Borrowing 2 Bits:
```
11111111.11111111.11111111.11|000000 = 255.255.255.192 (/26)
```

----------

### Step 3: Find the Increment

Use the chart to calculate the increment:

```
  1     1     0     0     0     0     0     0
|128 | 64  | 32  | 16  |  8  |  4  | 2  | 1  |
|256 | 128 | 64  | 32  | 16  |  8  | 4  | 2  |

``` 

✅ **The increment is 64**.

> By using the last hacked increment we can determine the size of each network block and what the ranges are.


### Step 4: Create Your /26 Networks (Subtract 1)

- Net 1   192.168.1.0 – 192.168.1.63
  
- Net 2   192.168.1.64 – 192.168.1.127
  
- Net 3   192.168.1.128 – 192.168.1.191
  
- Net 4   192.168.1.192 – 192.168.1.255 

----------------

### Step 5: How Many Hosts Are in Each Network?

New Subnet Mask:
```
255.255.255.192 = /26
```

```
          1     1    |  0    0    0    0     0    0
```

| Bit     | 128 | 64  | 32  | 16  | 8  | 4  | 2  | 1  |
|---------|-----|-----|-----|-----|----|----|----|----|
| Value   | 256 | 128 |  64 |  32 | 16 |  8 |  4 |  2 |


By using the chart and counting the number of network bits. We can determine the number of host for each network 64 total hosts and **62 usable hosts addresses.** Minus -2 (for the network addresss and broadcast).

------
## ☕ Subnet My Coffee Shop 

<img width="700" alt="image" src="https://github.com/user-attachments/assets/6a5e249a-3faa-4d3a-9f90-742eab65fbd2">

------
We need to create **3 separate networks**, each supporting **at least 40 hosts**.

### Given IP Address
The ISP has provided the following IP block:

- **Network Address:** `10.1.1.0/24`
- **Binary (Subnet Mask):** `11111111.11111111.11111111.00000000` = `255.255.255.0 (/24)`
- **Binary (IP Address):** `00001010.00000001.00000001.00000000` = `10.1.1.0`

-------
**Step 1:** Use the Nosferatz chart to calculate how many host bits we need to hack to meet the 40 hosts requirement


```
          1     1    |  0    0    0    0     0    0
```

| Bit     | 128 | 64  | 32  | 16  | 8  | 4  | 2  | 1  |
|---------|-----|-----|-----|-----|----|----|----|----|
| Value   | 256 | 128 |  64 |  32 | 16 |  8 |  4 |  2 |


> **We need to keep at 6 hosts bit to meet  40 hosts requirement**

-----
**Step 2: Hack the Host Bits** 

Original Subnet Mask (Binary):  

```
11111111.11111111.11111111.00000000 = 255.255.255.0 (/24)
```

New Subnet Mask After Borrowing 2 Bits:
```
11111111.11111111.11111111.11|000000 = 255.255.255.192 (/26)
```

------

**Step 3: Find the Increment**

Use the chart to calculate the increment:

```
  1     1     0     0     0     0     0     0
|128 | 64  | 32  | 16  |  8  |  4  | 2  | 1  |
|256 | 128 | 64  | 32  | 16  |  8  | 4  | 2  |

``` 

✅ **The increment is 64**.

> By using the last hacked increment we can determine the size of each network block and what the ranges are.

------
**Step 4: Create Your Network /26 (Subtract 1)**

- Net 1   10.1.1.0 – 10.1.1.63
  
- Net 2   10.1.1.64 – 10.1.1.127
  
- Net 3   10.1.1.128 – 10.1.1.191
  
- Net 4   10.1.1.192 – 10.1.1.255

-----
----------------

### Step 5: How Many Hosts Are in Each Network?

New Subnet Mask:
```
255.255.255.192 = /26
```

```
          1     1    |  0    0    0    0     0    0
```

| Bit     | 128 | 64  | 32  | 16  | 8  | 4  | 2  | 1  |
|---------|-----|-----|-----|-----|----|----|----|----|
| Value   | 256 | 128 |  64 |  32 | 16 |  8 |  4 |  2 |


By using the chart and counting the number of network bits. We can determine the number of host for each network:

- Each subnet provides **64 total host addresses**
- Out of those, **62 are usable host addresses**
- Minus -2 (for the network addresss and broadcast).

---------
## 💡 Nosferatz chart

| Bit     | 128 | 64  | 32  | 16  | 8  | 4  | 2  | 1  |
|---------|-----|-----|-----|-----|----|----|----|----|
| Value   | 256 | 128 |  64 |  32 | 16 |  8 |  4 |  2 |


> *The bottom row* tells us how many bits we need to hack based on the **host or network requirements**

> the top row tells us the increments used to calculate the **network address ranges**








