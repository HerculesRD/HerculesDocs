# Recoleccion de informacion
* [Informacion DNS](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#informacion-dns)
* [Correos](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Correos)
* [Tracking](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Tracking)
* [Buscadores](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Buscadores)
* [Cache](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Cache)
* [LAN](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#LAN)
* [Google Dorks](https://github.com/HerculesRD/HerculesDocs/tree/main/Recoleccion%20de%20informacion#Google-Dorks)

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

## Correos

### Pasivo

#### infoga

```bash
python infoga.py --domain www.url.com --source google -v 3 --breach
python infoga.py --info correo@domain.com
```

[Link Descarga](https://github.com/m4ll0k/infoga)

#### Google Mail Hunt (revision si sigue andando)

```bash
hunt mail@gmail.com
```

[Link Descarga](https://github.com/mxrch/GHunt)

### Trackeando mails

[Link registro servicio](https://getnotify.com/)

Como funciona: Te registras con el correo de origen y envias un correo a la direccion
que se quiere trackear con .getnotify.com al final. Si es gmail o hotmail no puede
verificar IP pero verifica si llego.

Ejemplo:

to: mail@dominio.com.getnotify.com

## Tracking

### Creando links para trackear - Grabify

[Link](https://grabify.link/)

## Buscadores

### Maltego

Aca deberia meter algo pero no se que.

### Buscadores de servicios

#### Shodan

[Link](https://www.shodan.io/)

### Busqueda generica

#### Yandex (muy buena para reverse image search)

[Yandex](https://www.shodan.io/)

#### Google

[Google](www.google.com)

[Google Dorks]()

### Personas

#### Oficial Argentina

[Buscar Personas](https://facuteayuda.com/buscar-datos-de-personas/)

### Buscador de API Keys

[KeyFinder](https://github.com/momenbasel/KeyFinder)

## Cache

* [CachedView](http://cachedview.com/)

* [Archive.org](https://archive.org/)


## LAN

```console
arp -a
```

## Google Dorks

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

### Backup y olds

```
site:www.url.com ext:bkf | ext:bkp | ext:bak | ext:old | ext:backup
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
site:pastebin.com | site:paste2.org | site:pastehtml.com | site:slexy.org | site:snipplr.com | site:snipt.net | site:textsnip.com | site:bitpaste.app | site:justpaste.it | site:heypasteit.com | site:hastebin.com | site:dpaste.org | site:dpaste.com | site:codepad.org | site:jsitor.com | site:codepen.io | site:jsfiddle.net | site:dotnetfiddle.net | site:phpfiddle.org | site:ide.geeksforgeeks.org | site:repl.it | site:ideone.com | site:paste.debian.net | site:paste.org | site:paste.org.ru | site:codebeautify.org  | site:codeshare.io | site:trello.com "www.url.com"
```

### Git

```
site:github.com | site:gitlab.com "www.url.com"
```

### Stack Overflow

```
site:stackoverflow.com "www.url.com"
```

