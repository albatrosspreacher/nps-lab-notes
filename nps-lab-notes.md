# NPS Lab - Important Points

Refer to [this Github Repository](https://github.com/ananyagupta6/NP-LAB) for all lab codes.

## Lab 1
> 5 components of a computer network -> Sender, Receiver, Message, Transmission medium, Protocols

A machine (client) makes a request to connect to another machine (server) for providing some service. The services running on the server run on known ports (application identifiers) and the client needs to know the address of the server machine and this port in order to connect to the server. On the other hand, the server does not need to know about the address or the port of the client at the time of connection initiation. The first packet which the client sends as a request to the server contains these information about the client which are further used by the server to send any information. Client (Active Open) acts as the active device which makes the first move to establish the connection whereas the server (Passive Open) passively waits for such requests from some client.


## Socket Programming

- Same machine: signals/pipes
- Different machine: sockets (full-duplex communication)
- Berkeley API for UNIX C
- Socket = IP Address + Port Number `192.168.1.2 49152`
- Communication services: TCP (Connection-oriented i.e. establish connection first) and UDP (Connectionless i.e. just transfer the data)
- TCP uses Stream Sockets (use when you need reliability in the connection) and UDP uses Datagrams 
- Use cases: TCP (file transfers, sending emails) and UDP (audio/video streaming)

### For TCP

Client: Create a socket, Establish a connection, Send/Receive data, Close the socket
Server: Create a socket, Bind the socket (attach a local address to the socket), Listen for requests, Accept a connection, Send/receive data, Close the socket

![](https://raw.githubusercontent.com/nandiniproothi/nps-lab-notes/main/img/tcp-socket.png?token=ALD5GB7QNU5FG2L2BTU3DMC754X7G)

### For UDP

Client: Create a socket, Send/Receive data
Server: Create a socket, Bind the socket (attach a local address to the socket), Send/receive data

![](https://raw.githubusercontent.com/nandiniproothi/nps-lab-notes/main/img/udp-socket.png?token=ALD5GB5GXJRLHBND25M2SG2754YFU)

### Header Files
- sys/types.h: defines socket address in unsigned long
- sys/socket.h: takes pointers to the socket address structure called sockaddr
- sys/netinet.h: defines IPv4 socket address structure called sockaddr_in
- arpa/inet.h: defines the macros used in netinet.h
- sys/stat.h
- netdb.h
- errno.h
- unistd.h 
- fcntl.h
- string.h
- stdlib.h
- stdio.h

> smol tip: in the client/server code that is provided in the lab, please add ```#include <arpa/inet.h>``` to compile it without errors.

### Structures
- sockaddr: address family, 14 bytes protocol-specific address
- sockaddr_in: address family, port, ip address, null
- in_addr: service port
- hostent: host name, aliases, address family, length of ip, internet address
- servent: service name, alias, port number, protocol

### Ports

Just don't go beyond 65535. Avoid reserved ports. Safe to use anything in the range `49151 - 65535`

### Byte Ordering

![](https://raw.githubusercontent.com/nandiniproothi/nps-lab-notes/main/img/byte-ordering.png?token=ALD5GB7MBKRK2S6XC2DM5AS754YII)

### IP Address Functions
- inet_aton
- in_addr_tinet_addr
- inet_ntoa
- connect
- bind
- listen
- accept
- send
- recv
- sendto
- recvfrom
- close
- shutdown

![](https://raw.githubusercontent.com/nandiniproothi/nps-lab-notes/main/img/def.png?token=ALD5GB3UCXOI6M3CHKUBLK2754YHG)

---

## Understanding Socket Programming Code

- Make sure you convert all data to a character/character array before passing it to the server/client side.
- Most functions return -1 in case of failure. Make sure you check for that condition

---

## Lab 2

---

## Lab 8

Packet Tracer Modes

- Logical (setup) and Physical (arrangement of buildings and all)
- Simulation (you can control packet transfer and other operations) and Realtime (sends packets on its own, like how it would do irl)

## Cables Used

- Cross-over: joins two networks of the same type (PC-PC, Router-Router)
- Straight-through: it's a type of twisted pair cable that is used to connect a computer to a network hub (router)

## CLI commands to configure a router
```
enable
configure terminal
interface fastethernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown

interface fastethernet 1/0
ip address 192.168.2.1 255.255.255.0
no shutdown

exit
```