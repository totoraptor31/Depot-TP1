# TP1

## EX1

##  Déterminer l'adresse MAC de vos deux machines

- show ip

## Définir une IP statique sur les deux machines

- PC1>ip 10.1.1.1/24 et PC2>ip 10.1.1.2/24 
NAME: PC1[1]
IP/MASK     : 10.1.1.1/24
GATEWAY     : 0.0.0.0
DNS         :
MAC         : 00:50:79:66:68:00
LPORT       : 10002
RHOST:PORT  : 127.0.0.1:10003
MTU:        : 1500

## Effectuer un ping d'une machine à l'autre

- ping 10.1.1.2

## Wireshark 
- Voir dans le depot git
## ARP

- show arp 00:50:79:66:68:01  10.1.1.2 expires in 113 seconds

## EX2

## Déterminer l'adresse MAC de vos trois machines

- show ip  MAC: 00:50:79:66:68:00


## Définir une IP statique sur les trois machines

- ip 10.1.1.3/24 

## Effectuer des ping d'une machine à l'autre

- PC1> ping 10.1.1.2
84 bytes from 10.1.1.2 icmp_seq=1 ttl=64 time=3.757 ms
84 bytes from 10.1.1.2 icmp_seq=2 ttl=64 time=3.057 ms
84 bytes from 10.1.1.2 icmp_seq=3 ttl=64 time=3.231 ms
84 bytes from 10.1.1.2 icmp_seq=4 ttl=64 time=4.317 ms
84 bytes from 10.1.1.2 icmp_seq=5 ttl=64 time=7.090 ms

PC2> ping 10.1.1.3
84 bytes from 10.1.1.3 icmp_seq=1 ttl=64 time=4.149 ms
84 bytes from 10.1.1.3 icmp_seq=2 ttl=64 time=3.525 ms
84 bytes from 10.1.1.3 icmp_seq=3 ttl=64 time=4.252 ms
84 bytes from 10.1.1.3 icmp_seq=4 ttl=64 time=3.608 ms
84 bytes from 10.1.1.3 icmp_seq=5 ttl=64 time=3.870 ms

PC1> ping 10.1.1.3
84 bytes from 10.1.1.3 icmp_seq=1 ttl=64 time=3.904 ms
84 bytes from 10.1.1.3 icmp_seq=2 ttl=64 time=4.299 ms
84 bytes from 10.1.1.3 icmp_seq=3 ttl=64 time=4.089 ms
84 bytes from 10.1.1.3 icmp_seq=4 ttl=64 time=5.049 ms
84 bytes from 10.1.1.3 icmp_seq=5 ttl=64 time=3.994 ms

## EX3

##  Donner un accès Internet à la machine dhcp.tp1.efrei

- ping google.com

PING google.com (142.250.179.110) 56(84) bytes of data.
64 bytes from par21s20-in-f14.1e100.net (142.250.179.110): icmp_seq=1 ttl=116 time=22.5 ms

##  Installer et configurer un serveur DHCP

PC1> dhcp -r
DORA
PC1> show ip

NAME        : PC1[1]
IP/MASK     : 10.1.1.10/24
GATEWAY     : 0.0.0.0
DNS         :
DHCP SERVER : 10.1.1.253
DHCP LEASE  : 479, 600/300/525
DOMAIN NAME : example.org
MAC         : 00:50:79:66:68:00
LPORT       : 20007
RHOST:PORT  : 127.0.0.1:20008
MTU         : 1500

## DHCP spoofing

### Configuration dnsmasq
port=0
interface=eth0
dhcp-range=10.1.1.210,10.1.1.250,12h

### Attribution de l'adresse IP par dnsmasq
PC1> dhcp
DDORA IP 10.1.1.246/24 DW 10.1.1.11



