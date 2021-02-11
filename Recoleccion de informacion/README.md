# Recoleccion de informacion
* [Informacion DNS](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#informacion-dns)
* [Correos](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Correos)
* [Tracking](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Tracking)
* [Buscadores](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Buscadores)
* [Cache](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Cache)
* [LAN](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#LAN)

## Informacion DNS

### Tools

#### whois

```bash
whois www.url.com
```

#### theHarvester

```bash
#baidu, bing, bingapi, bufferoverun, certspotter, crtsh, dnsdumpster,
#duckduckgo, exalead, github-code, google, hackertarget, hunter, intelx, 
#linkedin, linkedin_links, netcraft, otx, pentesttools, projectdiscovery,
#qwant, rapiddns, securityTrails, spyse, sublist3r, threatcrowd, threatminer,
#trello, twitter, urlscan, virustotal, yahoo

#l limita la cantidad de busquedas
#s es para usar shodan
theharvester -d www.url.com -l 500 -b google -s -f output.xml
```

[Link](https://github.com/laramies/theHarvester)

#### dmitry

```bash
dmitry -sei url.com
```

#### dnsrecon

```bash
dnsrecon -d url.com
```

#### nslookup

```bash
nslookup url.com
```

#### Photon

```bash
python3 photon.py -u www.url.com -l 10 #10 levels de crawl
--dns #enumera tambien subdominios y datos dns
```

### Web

* [Whois](https://who.is)
* [Netcraft](https://www.netcraft.com/)
* [WhatWeb](https://whatweb.net/)
* [Nmapper](https://www.nmmapper.com)
* [SecurityTrails](https://securitytrails.com/)
* [SpySe](https://spyse.com)
* [Pentest-Tools](www.pentest-tools.com)
* [DnsDumpster](https://dnsdumpster.com/)
* [PassiveDNS](passivedns.mnemonic.no)
* [URLScan](https://urlscan.io/)
* [Robtex](https://www.robtex.com/)
* [ICANN](https://lookup.icann.org/)

## Correos

## Tracking

## Buscadores

## Cache

## LAN