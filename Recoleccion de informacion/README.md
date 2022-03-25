# Recoleccion de informacion
* [Informacion DNS](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#informacion-dns)
* [Correos](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Correos)
* [Tracking](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Tracking)
* [Buscadores](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Buscadores)
* [Cache](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Cache)
* [LAN](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#LAN)
* [Google Dorks](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Google-Dorks)
* [Leaks](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Leaks)

## Informacion DNS

### Tools

* [whois](https://who.is/)

```bash
whois www.url.com
```

* [netograph](https://netograph.io/)
* [AnalyticsRelationships (Domains/Subdomains mirando Google Analytics)](https://github.com/Josue87/AnalyticsRelationships)
* [Frogy](https://github.com/iamthefrogy/frogy)

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

[Link descarga](https://github.com/laramies/theHarvester)

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
* [Phonebook](https://phonebook.cz/)

## Correos

### Pasivo

#### infoga

```bash
python infoga.py --domain www.url.com --source google -v 3 --breach
python infoga.py --info correo@domain.com
```

* [infoga](https://github.com/m4ll0k/infoga)

#### Google Mail Hunt (revision si sigue andando)

* [GHunt](https://github.com/mxrch/GHunt)

### Trackeando mails

[Link registro servicio](https://getnotify.com/)

Como funciona: Te registras con el correo de origen y envias un correo a la direccion
que se quiere trackear con .getnotify.com al final. Si es gmail o hotmail no puede
verificar IP pero verifica si llego.

Ejemplo:

to: mail@dominio.com.getnotify.com

### OSINT para correos

* [Buster](https://github.com/sham00n/buster)

## Telefonos

### Moriarty

```bash
#NO CORRERLO COMO ROOT
python3 moriarty.py -m correo@outlook.com -g correo@gmail.com -n +numeroTelefono
```

[Link Descarga](https://github.com/AzizKpln/Moriarty-Project)

## Tracking

### Creando links para trackear - Grabify

[Link](https://grabify.link/)

## Buscadores

### Maltego

Aca deberia meter algo pero no se que.

### Buscadores de servicios

* [Shodan](https://www.shodan.io/)
[karvaV2](https://github.com/Dheerajmadhukar/karma_v2) (Con Shodan API key premium)
* [Censys](https://censys.io/ipv4)
* [Zoomeye](https://www.zoomeye.org)
* [Greynose](https://viz.greynoise.io/)
* [Fofa](https://fofa.so)
* [PulseDive](https://pulsedive.com/)
* [15 tools inv](https://cipher387.github.io/domain_investigation_toolbox/ip.html?)

### Busqueda generica

* [Yandex](https://www.yandex.com/)
* [Google](www.google.com)
[Google Dorks](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Google-Dorks)
* [ZorexEye](https://zorexeye.com)

### Informacion variada

* [Buscar Personas](https://facuteayuda.com/buscar-datos-de-personas/)
* [Intelx](https://intelx.io/)
* [Maltiverse](https://maltiverse.com/)

### Correos

* [Hunter](https://hunter.io/)

### Buscador de API Keys

* [KeyFinder](https://github.com/momenbasel/KeyFinder)

### SSID

* [Wigle](https://wigle.net/)

## Cache

* [CachedView](http://cachedview.com/)
* [Archive.org](https://archive.org/)

## LAN

```console
arp -a
```

## Google Dorks

### Tools

* [GRecon](https://github.com/adnane-X-tebbaa/GRecon)
* [DorkSearch](https://dorksearch.com/)

### Subdominios

```
site:*.url.com

#Nested subdomains
site:*.*.*.url.com
```

### Documentos

```
site:www.url.com ext:doc | ext:docx | ext:odt | ext:rtf | ext:sxw | ext:psw | ext:ppt | ext:pptx | ext:pps | ext:csv
```

### Listado de directorios

```
site:www.url.com intitle:index.of
```

### Archivos de configuracion

```
site:www.url.com ext:xml | ext:conf | ext:cnf | ext:reg | ext:inf | ext:rdp | ext:cfg | ext:txt | ext:ora | ext:ini | ext:env
```

### Bases de datos

```
site:www.url.com ext:sql | ext:dbf | ext:mdb
```

### Logs

```
site:www.url.com ext:log
```

### Backup, devs y olds

```
site:www.url.com ext:bkf | ext:bkp | ext:bak | ext:old | ext:backup
```
```
inurl:"url.com" AND (staging | test | dev)
```

### Login

```
site:www.url.com inurl:login | inurl:signin | intitle:Login | intitle:"sign in" | inurl:auth
```

### Signup

```
site:www.url.com inurl:signup | inurl:register | intitle:Signup
```

### Errores SQL

```
site:www.url.com intext:"sql syntax near" | intext:"syntax error has occurred" | intext:"incorrect syntax near" | intext:"unexpected end of SQL command" | intext:"Warning: mysql_connect()" | intext:"Warning: mysql_query()" | intext:"Warning: pg_connect()"
```

### Errores PHP

```
site:www.url.com "PHP Parse error" | "PHP Warning" | "PHP Error"
```

### PHPinfo()

```
site:www.url.com ext:php intitle:phpinfo "published by the PHP Group"
```

### Pastebin simil

```
site:pastebin.com | site:paste2.org | site:pastehtml.com | site:slexy.org | site:snipplr.com | site:snipt.net | site:textsnip.com | site:bitpaste.app | site:justpaste.it | site:heypasteit.com | site:hastebin.com | site:dpaste.org | site:dpaste.com | site:codepad.org | site:jsitor.com | site:codepen.io | site:jsfiddle.net | site:dotnetfiddle.net | site:phpfiddle.org | site:ide.geeksforgeeks.org | site:repl.it | site:ideone.com | site:paste.debian.net | site:paste.org | site:paste.org.ru | site:codebeautify.org  | site:codeshare.io | site:trello.com | site:scribd.com | site:npmjs.com | site:npm.runkit.com | site:libraries.io "www.url.com"
```

### Sites 2

```
site:ycombinator.com | site:coggle.it | site:papaly.com | site:google.com | site:prezi.com | site:jsdelivr.net | site:codepen.io | site:codeshare.io | site:repl.it | site:productforums.google.com | site:gitter.im | site:bitbucket.org | site:zoom.us | site:atlassian.net "www.url.com"
```

### Git

```
site:github.com | site:gitlab.com | inurl:gitlab "www.url.com"
```

### Stack Overflow

```
site:stackoverflow.com "www.url.com"
```

### AmazonWS

```
site:s3.amazonaws.com inurl:"company"
```

## Leaks

* [pwndb](https://pwndb2am4tzkvold.tor2web.io/)
* [h8mail](https://github.com/khast3x/h8mail)
* [dehashed](https://dehashed.com/api)

## Identificacion de informacion

./pywhat [cualquierCosa] -> identifica que es el argumento pasado e informacion dentro
* [pywhat](https://github.com/bee-san/pyWhat)
