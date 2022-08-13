# DNS

### bash: one-liner forward lookup brute force
```bash
for ip in $(cat <file-name.txt>); do host $ip.<domain>; done | grep -v "not found"
```
---
### bash: one-liner reverse lookup brute force
```bash
for ip in $(sec 1 254); do host <aaa.bbb.ccc>.$ip; done | grep -v "not found"
```
---
### bash: List DSN servers
```bash
host -t ns <domain_name> | cut -d " " -f 4
```
---
### bash: DNS zone transfer
```bash
host -l <domain_name> <dns_server_address>
```
---
### dnsrecon: zone transfer
```bash
dnsrecon -d <domain_name> -t axfr
```
---
### dnsrecon: brute force
```bash
dnsrecon -d <domain_name> -D <word_list> -t brt
```
---
### dnsenum: DNS enumeration
```bash
dnsenum <domain_name>
```
---
### nmap: DNS zone transfer
```bash
nmap --script=dns-zone-transfer -p 53 <dns_server/domain>
```
---

# Ports

### nc: TCP scan with timeout (-w) and zero-I/O (-z)
```bash
nc -nvv -w <timeout_seconds> -z <ip> <port/port_range>
```
---
### nc: UDP scan with timeout (-w) and zero-I/O (-z)
```bash
nc -nv -u -z -w <timeout_seconds> <ip> <port/port_range>
```
---
### nmap: Top N ports TCP with NMAP
```bash
sudo nmap --top-ports <num_ports> -sC -sV <ip> --open --reason
```
---
### nmap: Full port range TCP (with banner grabbing and default scripts) using NMAP
```bash
sudo nmap -p- -sC -sV <ip> --open --reason
```
---
### nmap: TCP Connect scanning
```bash
nmap -sT <ip>
```
---
### nmap: Network sweep using NMAP
```bash
nmap -v -sn <aaa.bbb.ccc.1-254> -oG <file_name>
```
---
### nmap: UDP scan
```bash
sudo nmap -sU <ip>
```
---
### nmap: UDP + TCP SYN scan
```bash
sudo nmap -sS -sU <ip>
```
---
### nmap: Scan with banner grapping/service enumeration
```bash
nmap -sV -sT -A <ip>
```
---
### nmap: Network top N port sweep with OS, script and traceroute enabled, using NMAP
```bash
nmap -sT -A --top-ports=<num_ports> <aaa.bbb.ccc.1-254> -oG <file_name>
```
---
### nmap: OS (Operating System) Fingerprinting
```bash
sudo nmap -O <ip>
```
---
### masscan: scan port 80 of the whole subnet, e.g. class X subnet (not allowed in PWK lab)
```bash
sudo masscan -p80 <ip/mask> --rate=1000 -e <network_interface> --router-ip <router_ip>
```
---

# SMB

### nmap: SMB scan using NMAP
```bash
nmap -v -p 139,445 -oG <output_file> <ip/ip_range>
```
---
### nbtscan: SMB scan using nbtscan
```bash
sudo nbtscan -r <aaa.bbb.ccc.0/24>
```
---
### nmap: SMB scan using NMAP scripts
```bash
nmap -v -p 139,445 --script=smb-* <ip>
```
---
# NFS

### nmap: NFS simple scan using NMAP
```bash
nmap -v -p 111 <ip/ip_range>
```
---

### nmap: NFS scan with a banner and rpcinfo scripts using NMAP
```bash
nmap -sV -p 111 --script=rpcinfo <ip/ip_range>
```
---

### nmap: NSF scan with NSF scripts using NMAP
```bash
nmap -p 111 --script=nfs* <ip>
```
---

# SMTP

### nc: SMTP enumeration with netcat
```bash
nc -nv <ip> <port> # e.g.: nc -nv 10.10.1.10 25
VRFY <username>
EXPN <mailbox>
```
---

### python: SMTP enumeration using Python script
```python
#!/usr/bin/python3

import socket
import sys

if len(sys.argv) != 3:
    print("Usage: smtp-scan.py <ip> <username>")
    sys.exit(0)

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

connect = s.connect((sys.argv[1], 25))

banner = s.recv(1024)

print(banner)

cmd = "VRFY {}\r\n".format(sys.argv[2]);
s.send(cmd.encode())
result = s.recv(1024)

print(result)
s.close()
```
---

# SNMP

### nmap: SNMP scan for open ports
```bash
sudo nmap -sU --open -p 161 <aaa.bbb.ccc.1-254> -oG <output_file>
```
---

### onesixtyone: SNMP brute force attach against a list of IP addresses
```bash
onesixtyone -c <community_file> -i <ip_file>
```
---

### onesixtyone: example of possible SNMP community strings
```bash
public
private
manager
```
---

### snmpwalk: entire SNMP MIB tree enumeration
```bash
snmpwalk -c <community_string> -v1 -t <timeout_seconds> <ip>
```
---

### snmpwalk: SNMP enumerating Windows users
```bash
snmpwalk -c <community_string> -v1 <ip> 1.3.6.1.4.1.77.1.2.25
```
---

### snmpwalk: SNMP enumerating running Windows processes
```bash
snmpwalk -c <community_string> -v1 <ip> 1.3.6.1.2.1.25.4.2.1.2
```
---

### snmpwalk: SNMP enumerating open TCP ports
```bash
snmpwalk -c <community_string> -v1 <ip> 1.3.6.1.2.1.6.13.1.3
```
---

### snmpwalk: SNMP enumerating installed software
```bash
snmpwalk -c <community_string> -v1 <ip> 1.3.6.1.2.1.25.6.3.1.2
```
---

# VULNs

### nmap: vulnerability scanning
```bash
sudo nmap --script vuln <ip>
```
---
