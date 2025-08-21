# A Simple Makefile

![gnu_logo](gnu_logo.png)

This post presents a simple Makefile that can be used to build 2 programs. Its written to use implicit rules.

**<u><span>Prerequisties</span></u>**

To use this Makefile you need make and GCC. On Ubuntu 16.04.3:

Type **sudo apt-get update**

Type **sudo apt-get install build-essential**

**<u><span>Files</span></u>**

**Makefile**

```
CFLAGS += -Wall -g

all : \
	UDPEchoClient \
	UDPEchoServer

UDPEchoClient_objects = \
		UDPEchoClient.o \
		Practical.o

UDPEchoClient : $(UDPEchoClient_objects)

UDPEchoServer_objects = \
		UDPEchoServer.o \
		Practical.o

UDPEchoServer : $(UDPEchoServer_objects)

.PHONY : clean all
clean :
	rm -f UDPEchoClient $(UDPEchoClient_objects)
	rm -f UDPEchoServer $(UDPEchoServer_objects)
```

**UDPEchoClient.c**

```
#include 
#include 
#include 
#include 
#include 
#include 
#include "Practical.h"

int main(int argc, char *argv[]) {

	if (argc < 3 || argc > 4)
		DieWithUserMessage(
			"Parameter(s)",
		"  [ MAXSTRINGLENGTH)
		DieWithUserMessage(echoString, "string too long");

	char *servPort = (argc == 4) ? argv[3] : "echo";

	struct addrinfo addrCriteria;
	memset(&addrCriteria, 0, sizeof(addrCriteria));
	addrCriteria.ai_family = AF_UNSPEC;
	addrCriteria.ai_socktype = SOCK_DGRAM;
	addrCriteria.ai_protocol = IPPROTO_UDP;

	struct addrinfo *servAddr;
	int rtnVal = getaddrinfo(server, servPort, &addrCriteria, &servAddr);
	if (rtnVal != 0)
		DieWithUserMessage("getaddrinfo() failed",
				gai_strerror(rtnVal));

	int sock = socket(servAddr->ai_family, servAddr->ai_socktype,
			servAddr->ai_protocol);
	if (sock < 0)
		DieWithSystemMessage("socket() failed");

	ssize_t numBytes = sendto(sock, echoString, echoStringLen, 0,
			servAddr->ai_addr, servAddr->ai_addrlen);
	if (numBytes < 0)
		DieWithSystemMessage("sendto() failed");
	else if (numBytes != echoStringLen)
		DieWithUserMessage("sendto() error",
				"sent unexpected number of bytes");

	struct sockaddr_storage fromAddr;
	socklen_t fromAddrLen = sizeof(fromAddr);
	char buffer[MAXSTRINGLENGTH + 1];
	numBytes = recvfrom(sock, buffer, MAXSTRINGLENGTH, 0,
			(struct sockaddr *) &fromAddr, &fromAddrLen);
	if (numBytes < 0)
		DieWithSystemMessage("recvfrom() failed");
	else if (numBytes != echoStringLen)
		DieWithUserMessage("recvfrom() error",
				"received unexpected number of bytes");

	if (!SockAddrsEqual(servAddr->ai_addr, (struct sockaddr *) &fromAddr))
		DieWithUserMessage("recvfrom()",
				"received a packet from unknown source");

	freeaddrinfo(servAddr);

	buffer[echoStringLen] = '\0';
	printf("Received: %s\n", buffer);

	close(sock);
	exit(0);
}
```

**UDPEchoServer.c**

```
#include 
#include 
#include 
#include 
#include 
#include 
#include "Practical.h"

int main(int argc, char *argv[])
{
	if (argc != 2)
		DieWithUserMessage("Parameters(s)", "");

	char *service = argv[1];

	struct addrinfo addrCriteria;
	memset(&addrCriteria, 0, sizeof(addrCriteria));
	addrCriteria.ai_family = AF_UNSPEC;
	addrCriteria.ai_flags = AI_PASSIVE;
	addrCriteria.ai_socktype = SOCK_DGRAM;
	addrCriteria.ai_protocol = IPPROTO_UDP;

	struct addrinfo *servAddr;
	int rtnVal = getaddrinfo(NULL, service, &addrCriteria, &servAddr);
	if (rtnVal != 0)
		DieWithUserMessage("getaddrinfo() failed",
				gai_strerror(rtnVal));

	int sock = socket(servAddr->ai_family, servAddr->ai_socktype,
			servAddr->ai_protocol);
	if (sock < 0)
		DieWithSystemMessage("socket() failed");

	if (bind(sock, servAddr->ai_addr, servAddr->ai_addrlen) < 0)
		DieWithSystemMessage("bind() failed");

	freeaddrinfo(servAddr);

	for (;;) {
		struct sockaddr_storage clntAddr;
		socklen_t clntAddrLen = sizeof(clntAddr);

		char buffer[MAXSTRINGLENGTH];
		ssize_t numBytesRcvd = recvfrom(sock,
				buffer, MAXSTRINGLENGTH, 0,
				(struct sockaddr *) &clntAddr, &clntAddrLen);
		if (numBytesRcvd < 0)
			DieWithSystemMessage("recvfrom() failed");

		fputs("Handling client ", stdout);
		PrintSocketAddress((struct sockaddr *) &clntAddr, stdout);
		fputc('\n', stdout);

		ssize_t numBytesSent = sendto(sock, buffer, numBytesRcvd, 0,
				(struct sockaddr *) &clntAddr,
				sizeof(clntAddr));
		if (numBytesSent < 0)
			DieWithSystemMessage("sendto() failed");
		else if (numBytesSent != numBytesRcvd)
			DieWithUserMessage("sendto()",
				"sent unexpected number of bytes");
	}
}
```

**Practical.c**

```
#include 
#include 
#include 
#include 
#include 
#include 

void PrintSocketAddress(const struct sockaddr *address, FILE *stream) {
	if (address == NULL || stream == NULL)
		return;

	void *numericAddress;

	char addrBuffer[INET6_ADDRSTRLEN];
	in_port_t port;
	switch (address->sa_family) {
		case AF_INET:
		numericAddress = &((struct sockaddr_in *) address)->sin_addr;
		port = ntohs(((struct sockaddr_in *) address)->sin_port);
		break;
		case AF_INET6:
		numericAddress = &((struct sockaddr_in6 *) address)->sin6_addr;
		port = ntohs(((struct sockaddr_in6 *) address)->sin6_port);
		break;
		default:
		fputs("[unknown type]", stream);
		return;
	}

	if (inet_ntop(address->sa_family, numericAddress, addrBuffer,
				sizeof(addrBuffer)) == NULL)
		fputs("[invalid address]", stream);
	else {
		fprintf(stream, "%s", addrBuffer);
		if (port != 0)
			fprintf(stream, "-%u", port);
	}
}

int SockAddrsEqual(struct sockaddr *addr1, struct sockaddr *addr2) {
	if (addr1 == NULL || addr2 == NULL)
		return addr1 == addr2;
	else if (addr1->sa_family != addr2->sa_family)
		return 0;
	else if (addr1->sa_family == AF_INET) {
		struct sockaddr_in *ipv4Addr1 = (struct sockaddr_in *) addr1;
		struct sockaddr_in *ipv4Addr2 = (struct sockaddr_in *) addr2;
		return ipv4Addr1->sin_addr.s_addr == ipv4Addr2->sin_addr.s_addr
			&& ipv4Addr1->sin_port == ipv4Addr2->sin_port;
	} else if (addr1->sa_family == AF_INET6) {
		struct sockaddr_in6 *ipv6Addr1 = (struct sockaddr_in6 *) addr1;
		struct sockaddr_in6 *ipv6Addr2 = (struct sockaddr_in6 *) addr2;
		return memcmp(&ipv6Addr1->sin6_addr, &ipv6Addr2->sin6_addr,
			sizeof(struct in6_addr)) == 0 &&
			ipv6Addr1->sin6_port == ipv6Addr2->sin6_port;
	} else
		return 0;
}

void DieWithUserMessage(const char *msg, const char *detail) {
	fputs(msg, stderr);
	fputs(": ", stderr);
	fputs(detail, stderr);
	fputc('\n', stderr);
	exit(1);
}

void DieWithSystemMessage(const char *msg) {
	perror(msg);
	exit(1);
}
```

**Practical.h**

```
#ifndef PRACTICAL_H                                                             
#define PRACTICAL_H                                                             
                                                                                
#define MAXSTRINGLENGTH 256                                                     
                                                                                
void PrintSocketAddress(const struct sockaddr *address, FILE *stream);          
int SockAddrsEqual(struct sockaddr *addr1, struct sockaddr *addr2);             
                                                                                
void DieWithUserMessage(const char *msg, const char *detail);                   
void DieWithSystemMessage(const char *msg);                                     
                                                                                
#endif /* PRACTICAL_H */
```

**<u><span>Usage</span></u>**

Copy everything into one directory

Type **make** to clean and build everything

Type **make all** to build everything

Type **make clean** to clean everything

<u><span>Run It</span></u>

Type **./UDPEchoServer 49152** in one terminal

Type **./UDPEchoClient localhost "Hello!" 49152** repeatedly in another terminal

**<u><span>References</span></u>**

-   This code is from p. 54-59 of TCP/IP Sockets in C: Practical Guide for Programmers (The Morgan Kaufmann Practical Guides Series) 2nd Edition \[[<u><span>Amazon</span></u>](https://www.amazon.com/TCP-IP-Sockets-Practical-Programmers/dp/0123745403)\] and \[[<u><span>link</span></u>](http://cs.baylor.edu/~donahoo/practical/CSockets2/code/code/AddressUtility.c)\]
    
-   GNU image from \[[<u><span>link</span></u>](https://en.wikipedia.org/wiki/GNU_Project)\]