# [ifconfig](https://linux.die.net/man/8/ifconfig) - interface configurator

Initialize an interface, configure it with an IP address, and enable or disable it. It is also used to display the route and the network interface.

Info that can be gathered:

- IP address
- MAC address
- MTU(Maximum Transmission Unit) 

Show all interfaces and its info.
```bash
ifconfig
```

Assign an IP address and Gateway to an interface
```bash
ifconfig eth0 <address> netmask <address> 
```

To enable an interface
```bash
ifup eth0 
```

To disable an interface
```bash
ifdown eth0 
```

To set the size of MTU
```bash
Ifconfig eth0 mtu xxxx
```

# ip - latest and updated version of ifconfig command

To set the size of MTU
```bash
ip a show
```

# Traceroute

Detects the delay and determines the pathway to your target.

- Provides the names and identifies every device on the path. 
- Follows the route to the destination
- Determines where the network latency comes from and reports it.

Command:
```bash
traceroute <destination>
```

Output provides:

- The specified hostname
- Size of the packets
- The maximum number of hops required.
- The IP address.

Indicates network delays. Asterisks indicates a potential problem in reaching that host. It indicates packet loss during communication to the network.

Command:
```bash
traceroute -n <destination>
```

Normally, traceroute sends UDP packets. It can also send TCP or ICMP packets.

Send in ICMP

Command:
```bash
sudo traceroute -I <destination>
```
Send in TCP

Command:
```bash
sudo traceroute -T <destination>
```

# Tracepath

Detect network delays. (Does not need root unlike traceroute)

Command:
```bash
tracepath <destination> 
```

# Ping - Packet INternet Groper

Checks for the network connectivity between two nodes.


```bash
ping <destination> 
```

Limit the number of packets
```bash
ping -c <number> <destination>
```

# Netstat - network statistics

Open sockets, routing tables, and connection information.


Show all open sockets

```bash
netstat
```

Show all open sockets

```bash
netstat
```

Display programs 

```bash
netstat -p 
```

Show statistics of all the ports
```bash
netstat -s
```

Information of the routing table 
```bash
netstat -r
```

# SS - replacement for netstat command

TCP, UDP, and UNIX socket connections. Combine with -a to show connected and listening sockets.  (-t, -u, -x)
```bash
ss -ta 
```
```bash
ss -ua  
```
```bash
ss -xa 
```
Show only the listening sockets
```bash
ss -lt 
```
```bash
ss -lu 
```
```bash
ss -lx
```
established sockets of TCP for IPV4
```bash
ss -t4 state established
```
list of all closed TCP sockets
```bash
ss -t4 state closed
```
list of all connected ports for a specific IP address
```bash
ss dst XXX.XXX.XXX.XXX
```

# Dig - Domain Information Groper

Used for:

- DNS lookup to query the DNS name server.
- Troubleshoot DNS related issues.
- Verify DNS mappings, MX Records, host addresses, and all other DNS records for a better understanding of the DNS topography.

```bash
dig <domainName> 
```

Outputs the A records by default. 

- MX, NS or any type

```bash
dig <domainName>  MX
```

```bash
dig <domainName> NS
```
```bash
dig <domainName> ANY
```

# nslookup - older version of dig.
```bash
nslookup <domainName>
```

# route
Displays and manipulates the routing table (find the best way to send the packets across to a destination).


```bash
route
```
Any packets whch outside the network range will be forwarded to the default gateway.

Displaying numerical IP address
```bash
route -n
```

Add a gateway
```bash
route add default gw <IP address> 
```

Kernel maintains all the routing cache information in a table for faster routing. To list the routing cache information, use the following command.


```bash
 route -Cn 
```
#Arp

Table of IP addresses and their corresponding MAC addresses. Router will check for the MAC address in this table. If it is cached, the table will not be used.


```bash
arp -n
```
Delete entries
```bash
arp -d HWADDR
```

# Curl & Wget
Fetch files
```bash
curl -O <fileLink>
```

```bash
wget <fileLink> 
```

# MTR - combination of ping and the traceroute command

```bash
mtr <path>
```


# TCPDUMP
Captures the traffic that is passing through the network interface and displays it. 


```bash
tcpdump -i <network_device>
```
Specify the protocol (TCP, UDP, ICMP, and others) 
```bash
tcpdump -i <network_device> tcp
```

Specify number of events
```bash
tcpdump -c 20 -i <network_device>
```

Specify the IP you are capturing from
```bash
tcpdump -c 20 -i <network_device> src XXX.XXX.XXX.XXX
```
Save to file 
```bash
tcpdump -w /path/ -i <network_device>
```
Read from file
```bash
tcpdump -r /path
```

## [Reference](https://mindmajix.com/linux-networking-commands-best-examples)




