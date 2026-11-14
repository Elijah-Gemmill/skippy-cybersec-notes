# Nmap

Nmap is an essential tool for network and service enumeration. It allows using multiple network protocols, though TCP is most typical. 

Synopsis: nmap [ \<Scan Type> ...] [ \<Options> ] { \<target specification> }

### Scan types

There are a number of scan types which decide the protocol and nature of the scan. 
They include:
- -sS - TCP SYN scan - Sends a SYN packet and waits for response, but does not complete TCP handshake
- -sT - TCP Connect Scan - Completes a full TCP handshake, then cancels the connection with a RST packet.
- -sA - TCP ACK Scan - Sends only an ACK packet, can be used to check firewalls
- -sV - Service Detection - After checking the TCP connection, Nmap probes for service types, versions, hostname, and OS - Requires Sudo permissions
- -sU - UDP Scan - Scans for open UDP ports
- -sC - Script Scan - Performs scan with default scripts - can be used in place of -sV when it times out.
- --script \<script\> - Performs script scan with a specified script or set of scripts.
- -O - Performs OS detection

### Options

In addition to scan types, you can also use different options to alter Nmap behavior. 
These include:
- -p\<port range> - Specifies a port range to scan. Can be a single port, or be a set of ports defined with a - like 1-443
- -p- - Scans all possible ports
- -T\<0-5\> - Specifies a rate, 0 for very slow, 5 for extremely fast (4 is recommended as a maximum)

### Target Specification

Nmap requires a target for its scan, which must be specified as the final argument of the command

A singular IP may be specified
- nmap -sV 192.168.1.1

But you may also specify an IP range with CIDR notation 
- nmap -sV 192.168.0.0/16