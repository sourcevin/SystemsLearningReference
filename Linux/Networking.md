### Basic to advanced networks

#### binary to decimal

`11111111 = 1*128+ 1*64 + 1*32+ 1*16+ 1*8+ 1*4 + 1*2 + 1*1 = 255`

#### decimal to binary
```
255 = 

255/2 =  127 ==> 1
127/2 =  63  ==> 1
63/2  =  31  ==> 1
31/2  =  15  ==> 1
15/2  =   7  ==> 1
7/2   =   3  ==> 1
3/2   =   1  ==> 1
1/2   =   0  ==> 1

11111111
```

##### IP and subnet mask
```
 108           161       228       70
01101100     10100001   11100100   01000110

11111111     11111111   11110000   00000000
255            255       240         0
```

The subnet mask indicates what part of the IP address is network and what part is host. here there are 4096 address. first one is network address and last one is broadcast address

```
IP Address:	108.161.228.70
Network Address:	108.161.224.0
Usable Host IP Range:	108.161.224.1 - 108.161.239.254
Broadcast Address:	108.161.239.255
Total Number of Hosts:	4,096
Number of Usable Hosts:	4,094
Subnet Mask:	255.255.240.0
Wildcard Mask:	0.0.15.255
Binary Subnet Mask:	11111111.11111111.11110000.00000000
IP Class:	B
CIDR Notation:	/20
IP Type:	Public
Short:	108.161.228.70 /20
Binary ID:	01101100101000011110010001000110
Integer ID:	1822549062
Hex ID:	0x6ca1e446
in-addr.arpa:	70.228.161.108.in-addr.arpa
IPv4 Mapped Address:	::ffff:6ca1.e446
6to4 Prefix:	2002:6ca1.e446::/48
```
