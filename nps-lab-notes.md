# NPS Lab - Important Points

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

[](https://github.com/nandiniproothi/nps-lab-notes/blob/main/img/tcp-socket.png?raw=true)

### For UDP

Client: Create a socket, Send/Receive data
Server: Create a socket, Bind the socket (attach a local address to the socket), Send/receive data

[](https://github.com/nandiniproothi/nps-lab-notes/blob/main/img/tcp-socket.png?raw=true)

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

[](https://github.com/nandiniproothi/nps-lab-notes/blob/main/img/byte-ordering.png?raw=true)

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

[](https://github.com/nandiniproothi/nps-lab-notes/blob/main/img/def.png?raw=true)

---

## Understanding Socket Programming Code

Refer to [this Github Repository](https://github.com/ananyagupta6/NP-LAB) for all lab codes.

- Make sure you convert all data to a character/character array before passing it to the server/client side.
- Most functions return -1 in case of failure. Make sure you check for that condition