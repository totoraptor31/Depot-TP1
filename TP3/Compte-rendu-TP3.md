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

# Partie 2

- ## VLAN
### ping PC1 et PC3
```
PC1> ping 10.3.1.2

84 bytes from 10.3.1.2 icmp_seq=1 ttl=64 time=2.585 ms
84 bytes from 10.3.1.2 icmp_seq=2 ttl=64 time=3.024 ms
```
## Routeur

### Ping LAN1 vers LAN2
```
PC1> show ip

NAME        : PC1[1]
IP/MASK     : 10.3.1.1/24
GATEWAY     : 10.3.1.254

PC1> ping 10.3.2.1

10.3.2.1 icmp_seq=1 timeout
84 bytes from 10.3.2.1 icmp_seq=2 ttl=63 time=13.565 ms
84 bytes from 10.3.2.1 icmp_seq=3 ttl=63 time=20.213 ms
```
### Ping vers internet
```
PC1> ping 8.8.8.8

84 bytes from 8.8.8.8 icmp_seq=1 ttl=59 time=41.582 ms
84 bytes from 8.8.8.8 icmp_seq=2 ttl=59 time=39.194 ms
```
# Partie III.

## DHCP

```
PC2> ip dhcp
DDORA IP 10.3.2.2/24 GW 10.3.2.254

PC2> show ip

NAME        : PC2[1]
IP/MASK     : 10.3.2.2/24
GATEWAY     : 10.3.2.254
DNS         : 1.1.1.1  
DHCP SERVER : 10.3.2.253
DHCP LEASE  : 596, 600/300/525
MAC         : 00:50:79:66:68:01
LPORT       : 20023
RHOST:PORT  : 127.0.0.1:20024
MTU         : 1500

PC2> ping efrei.fr
efrei.fr resolved to 51.255.68.208

84 bytes from 51.255.68.208 icmp_seq=1 ttl=59 time=41.093 ms
84 bytes from 51.255.68.208 icmp_seq=2 ttl=59 time=36.789 ms
```

## DNS


### Ping de ```efrei.fr``` et ```dns.tp3.b2```
```
PC2> ping efrei.fr
efrei.fr resolved to 51.255.68.208

84 bytes from 51.255.68.208 icmp_seq=1 ttl=247 time=30.448 ms
84 bytes from 51.255.68.208 icmp_seq=2 ttl=247 time=28.354 ms
^C
PC2> ping dns.tp3.b2
dns.tp3.b2 resolved to 10.3.3.1

84 bytes from 10.3.3.1 icmp_seq=1 ttl=63 time=19.614 ms
84 bytes from 10.3.3.1 icmp_seq=2 ttl=63 time=20.926 ms
```

### [Capture requête DNS](./RequeteDNS.pcapng)

## HTTP

### Visite du site ```web.tp3.b2```
```
curl http://web.tp3.b2
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

### Visite du site ```supersite.tp3.b3```

```
curl http://supersite.tp3.b2
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

# Partie IV.

## DNS

### Enregistrement AXFR ```tp3.b2```
```
> tp3.b2
Server:         10.3.3.1
Address:        10.3.3.1#53

tp3.b2
        origin = dns.tp3.b2
        mail addr = admin.tp3.b2
        serial = 2019061800
        refresh = 3600
        retry = 1800
        expire = 604800
        minimum = 86400
tp3.b2  nameserver = dns.tp3.b2.
Name:   coolsite.tp3.b2
Address: 10.3.3.4
Name:   dns.tp3.b2
Address: 10.3.3.1
Name:   meow.tp3.b2
Address: 10.3.3.6
Name:   prout.tp3.b2
Address: 10.3.3.5
Name:   supersite.tp3.b2
Address: 10.3.3.2
Name:   web.tp3.b2
Address: 10.3.3.2
Name:   web2.tp3.b2
Address: 10.3.3.4
Name:   web3.tp3.b2
Address: 10.3.3.5
Name:   web4.tp3.b2
Address: 10.3.3.6
tp3.b2
        origin = dns.tp3.b2
        mail addr = admin.tp3.b2
        serial = 2019061800
        refresh = 3600
        retry = 1800
        expire = 604800
        minimum = 86400
```

### Extrait du shell SSH
-bash: je : commande introuvable
 hclient_loop: send disconnect: Broken pipe
