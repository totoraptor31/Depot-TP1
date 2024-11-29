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

##  Installer et configurer un serveur DHCP





