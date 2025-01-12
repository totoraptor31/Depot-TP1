## TP3

# Partie 1

- ping d'un client du  LAN1 vers un client du LAN 2

PC1> ping 10.3.2.1

84 bytes from 10.3.2.1 icmp_seq=1 ttl=62 time=40.921 ms
84 bytes from 10.3.2.1 icmp_seq=2 ttl=62 time=27.896 ms
84 bytes from 10.3.2.1 icmp_seq=3 ttl=62 time=38.439 ms
84 bytes from 10.3.2.1 icmp_seq=4 ttl=62 time=34.284 ms
84 bytes from 10.3.2.1 icmp_seq=5 ttl=62 time=33.392 ms

-  Afficher les adresses MAC des routeurs

R1#sh arp
Protocol  Address          Age (min)  Hardware Addr   Type   Interface
Internet  10.3.12.1               -   c401.068c.0001  ARPA   FastEthernet0/1
Internet  10.3.12.2              38   c402.06aa.0001  ARPA   FastEthernet0/1
Internet  10.3.1.1                1   0050.7966.6800  ARPA   FastEthernet0/0
Internet  10.3.1.2               20   0050.7966.6801  ARPA   FastEthernet0/0
Internet  192.168.122.1           7   5254.0023.04c2  ARPA   FastEthernet1/0
Internet  192.168.122.92          -   c401.068c.0010  ARPA   FastEthernet1/0
Internet  10.3.1.254              -   c401.068c.0000  ARPA   FastEthernet0/0
R2#sh arp
Protocol  Address          Age (min)  Hardware Addr   Type   Interface
Internet  10.3.12.1              38   c401.068c.0001  ARPA   FastEthernet0/1
Internet  10.3.12.2               -   c402.06aa.0001  ARPA   FastEthernet0/1
Internet  10.3.2.1                1   0050.7966.6802  ARPA   FastEthernet0/0
Internet  10.3.2.254              -   c402.06aa.0000  ARPA   FastEthernet0/0

-  Prouvez que vous avez déjà un accès internet sur r1

R1#ping 8.8.8.8

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 8.8.8.8, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 60/62/68 ms
R1#

- Accès internet LAN1

PC1> ping 8.8.8.8

84 bytes from 8.8.8.8 icmp_seq=1 ttl=114 time=40.056 ms
84 bytes from 8.8.8.8 icmp_seq=2 ttl=114 time=39.436 ms
84 bytes from 8.8.8.8 icmp_seq=3 ttl=114 time=39.333 ms
84 bytes from 8.8.8.8 icmp_seq=4 ttl=114 time=40.002 ms
84 bytes from 8.8.8.8 icmp_seq=5 ttl=114 time=35.909 ms

 Accès internet LAN2


PC3> ping 8.8.8.8

84 bytes from 8.8.8.8 icmp_seq=1 ttl=113 time=53.097 ms
84 bytes from 8.8.8.8 icmp_seq=2 ttl=113 time=49.373 ms
84 bytes from 8.8.8.8 icmp_seq=3 ttl=113 time=50.980 ms
84 bytes from 8.8.8.8 icmp_seq=4 ttl=113 time=45.966 ms
