## Operadores
```bash
ip && ip
ip and ip
ip xor ip
ip ^^ ip (xor)
not ip
!ip (not)

ip eq ip
ip == ip
ip != ip
ip ne ip
ip > ip
ip gt ip
ip < ip 
ip lt ip
ip >= ip
ip ge ip
ip <= ip
ip le ip
```

## Protocolos
```bash
ether
fddi
ip
arp
rarp
decnet
lat
sca
moprc
mopdl
tcp
udp
```

## Filtros
```bash
ip.addr == 127.0.0.1
ip.dest == 127.0.0.1
ip.src == 127.0.0.1
tcp.port == 25
tcp.dstport == 23
http.host == "host name"
frame.time >= "June 02, 2019 18:04:00"
tcp.flags.syn == 1 and tcp.flags.ack == 0
wlan.fc.type_subtype = 0x08 -> beacon filter
eth.dst -- ff:ff:ff:ff:ff:ff -> broadcast filter
(eth.dst[0] & 1) -> multicast filter
ip.host = hostname
eth.addr == <macaddress>
```

