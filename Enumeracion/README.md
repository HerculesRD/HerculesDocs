# Enumeracion

1. [Nmap](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#Nmap)
	* [Objetivos](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#objetivos)
	* [Descubrimiento](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#Descubrimiento)
	* [Puertos](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#Puertos)
	* [Versiones](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#Versiones)
	* [Salida](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#Salida)
	* [Salteando escudos](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#Salteando-escudos)
	* [Scripts](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#scripts)
	* [Opciones Adicionales](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#opciones-adicionales)
2. [Amass](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#Amass)
3. [Descubrimiento de dir & files](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#descubrimiento-de-dir--files)
	* [Tips & Tricks](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#tips--tricks-2)
	* [Fuzzers](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#Fuzzers)
	* [Parametros HTTP](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#parametros-http)
	* [VHosts](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#vhosts)
4. [Escaneres y enumeracion](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#escaner-y-enumeracion)
	* [Escaneando S.O.](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#escaneando-so)
	* [Escaneando WAFs](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#escaneando-wafs)
	* [Buscando metadatos online](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#buscando-metadatos-online)
	* [Escaneando SMB](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#escaneando-smb)
	* [Escaneando LDAP](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#escaneando-ldap)
	* [Escaneando RPC](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#escaneando-rpc)
	* [Escaneando SNMP](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#escaneando-snmp)
	* [Escaneando MSSQL](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#escaneando-mssql)
	* [Escaneando RDP](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#escaneando-rdp)
	* [Git grabber](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#git-grabber)
	* [Escaner XSS](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#escaner-xss)
	* [Escaner CRLF](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#escaner-crlf)
	* [Escaner CSRF](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#escaner-csrf--xsrf)
	* [Escaner SSL](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#escaner-ssl)
	* [POP3](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#pop3)
5. [Web scanners](https://github.com/HerculesRD/HerculesDocs/tree/main/Enumeracion#web-scanners)

# Nmap

## Objetivos

```bash
nmap 192.168.1.2
nmap 192.168.1.2-10
nmap 192.168.1-10.2-10
nmap 192.168.1.2/24
nmap scanme.nmap.org
nmap scanme.nmap.org --resolve-all
nmap -iL hosts.txt
nmap -iL hosts.txt --exclude 192.168.0.1
nmap -iL hosts.txt --excludefile estasNo.txt
```

## Descubrimiento

### Tips & Tricks

```bash
--disable-arp-ping #deshabilita el ARP para poder hacer escaneos mas fieles
-sn # no escanear puertos
--discovery-ignore-rst #Ignora el RST para tener resultados reales a pesar de FW
-sL #solo lista objetivos, no hace ruido en la red
-n #no resolver
-O #Sistemas Operativos
--randomize-hosts
```

### TCP

```bash
nmap 192.168.1.2 -PS
```

### UDP

```bash
nmap 192.168.1.2 -PU
```

### ACK

```bash
nmap 192.168.1.2 -PA
```

### SCTP Init

Solo para los que admiten protocolo SCTP
```bash
nmap 192.168.1.2 -PY
```

### Echo Ping

Vacio a comparacion del ping comun
```bash
nmap 192.168.1.2 -PE
```

### Timestamp Request

```bash
nmap 192.168.1.2 -PP
```

### Address Mask request

Generalmente ignorado por kernel, quizas para routers
```bash
nmap 192.168.1.2 -PM
```

### Protocol ping

```bash
nmap 192.168.1.2 -PO <Num protocolo>

#Buscamos los numeros de protocolos con
#cat /usr/share/nmap/nmap-protocols
```

## Puertos

### Tips & Tricks

```bash
-Pn #No hacer Ping
-p20,21,22-24
--exclude-ports <ports>
--max-retries 0 #Por defecto 1, puede aumentar si hay congestion de red
-r #Hacer el escaneo secuencial en vez de aleatorio
--top-ports <Num> #Num puertos mas comunes
-F #FAST: los 1000 puertos mas comunes
--port-ratio <ratio> #escanear todos los puertos del 
#archivo nmap-services con un ratio igual o mayor que <ratio>.
#<ratio> tiene que ser un valor entre 0.0 y 1.0

open #Responde o parece abierto
closed #Responde con un error
filtered #No responde, anomalia
unfiltered #No puede determinar el estado pero responde
open | filtered #No puede determinar el estado por no responder
```

### TCP

```bash
nmap 192.168.1.2 -sT
```

### SYN

Mas rapido que el anterior
```bash
nmap 192.168.1.2 -sS
```

### ACK

Respuesta como unfiltered o filtered
```bash
nmap 192.168.1.2 -sA
```

### SCTP Init Scan

Responde open, closed, filtered
```bash
nmap 192.168.1.2 -sY
```

### SCTP Cookie Echo Scan

A veces los fw saltean filtrar este scan pero solo sabe si closed u open/filtered

```bash
nmap 192.168.1.2 -sZ
```

### Abusando de RFC TCP

Todo puerto cerrado que reciba un paquete sin el flag "RST" debe contestar con un
paquete TCP "RST".

Responden con: Cerrado, abierto|filtrado o filtrado.

Solo sirve para saber si existe un firewall y que tan fiable es

#### Maimon

FIN/ACK

```bash
nmap 192.168.1.2 -sM
```

#### Null

no flags
```bash
nmap 192.168.1.2 -sn
```

#### XMas

FIN, PSH y URG
```bash
nmap 192.168.1.2 -sX
```

#### FIN

FIN
```bash
nmap 192.168.1.2 -sF
```

### ScanFlags

Se pueden agregar todas las flags que quieran de entre:
SYN, URG, ACK, PSH, RST, FIN
```bash
nmap 192.168.1.2 --scanflags SYNURG
```

Se puede agregar un tipo de scan para saber como interpretar la respuesta
```bash
nmap 192.168.1.2 --scanflags SYNURG -sS
```

## Versiones

```bash
nmap 192.168.1.2 -sV

nmap 192.168.1.2 -sV --allports #incluir todos los puertos para la deteccion de versiones
nmap 192.168.1.2 -sV --version-intesity 9 #entre 0 y 9, el default es 7
```

## Salida

```bash
nmap 192.168.1.2 -oN #nmap
nmap 192.168.1.2 -oX #XML
nmap 192.168.1.2 -oG #grepeable
nmap 192.168.1.2 -oA #Todos
```

## Salteando escudos

```bash
nmap 192.168.1.2 -f #fragmentado de paquetes
nmap 192.168.1.2 --source-port 80 #puerto de origen
nmap 192.168.1.2 --data-length 300 #para darle una cierta longitud al paquete y no sea vacio
nmap 192.168.1.2 --badsum 
```
## Scripts

```bash
nmap 192.168.1.2 --script=vuln
#Categorias: auth, broadcast, brute, default, discovery, dos, exploit, external, fuzzer
#intrusive, malware, safe, version, vuln
nmap 192.168.1.2 --script-updatedb #actualiza db si metemos un nuevo script
```
## Opciones Adicionales

```bash
nmap 192.168.1.2 --traceroute
nmap 192.168.1.2 --system-dns #usar el dns del sistema
nmap 192.168.1.2 --dns-servers <dns-server> #usar un dns especifico
nmap 192.168.1.2 -ddddddddddd #debugging
nmap -6 #usar ipv6
nmap -T0 #de 0 a 5 el tiempo de escaneo. 5 es el mas rapido
```

# Amass

# Descubrimiento de dir & files

## Tips & Tricks

### Encontrando dirs

```
Si encontramos un directorio, podemos buscar directorios relacionados parecidos. Por ejemplo:
/addpassword → /getpassword /updatepassword /forgotpassword /adduser
```

### Bypassing codes / denies / forbidden

```
Si HTTPS o HTTP /directory/ -> 403 forbidden
Cambiar a HTTP o HTTPS -> 200
```

```
GET /admin HTTP/1.1
Host: http://site.com
—-
Access is denied
———————————
GET /test HTTP/1.1
Host: http://site.com
X-Original-URL: /admin
—-
HTTP/1.1 200 OK
```

### Redirecciones

```
Cuando codigo es 302 y size response > 1kb es sospechoso
Interceptamos con proxy la respuestas y tenemos 
301/302 y location (para saber a donde redirigir)
Cambiamos 301/302 a 200 para tener un nuevo resultado que antes no teniamos
```

## Fuzzers

### Ffuf

```bash
ffuf -u www.url.com/FUZZ -w wordlist.lst
ffuf -w wordlist.lst -u url.com -H “Host: FUZZ.url.com”
ffuf -e .php,.txt,.aspx #extensiones
ffuf -mc 200 #match status code
ffuf -ml 200 #match cantidad de lineas
ffuf -mr #match regex
ffuf -ms #match size response
ffuf -mw #match cantidad de palabras
ffuf -fw #filtrar por cantidad de palabras
ffuf -fl #filtrar por cantidad de lineas
ffuf -fs #filtrar por size response
ffuf -fc #filtrar por status code
ffuf -fr #filtrar por regex
ffuf -c #agregarle colorcito a la salida
ffuf -recursion #recursivo
ffuf -recursion-depth 2 #nivel de recursion (va solo sin el anterior)
```

### Gobuster

```bash
gobuster dir -u www.url.com -w wordlist.lst
```

### DNSMap

```bash
dnsmap dominios.txt
```

### Sublist3r

```bash
sublist3r -d www.url.com 
```

### Nmap

```bash
nmap -p80,443 --script dns-brute
```

### dirsearch

```bash
dirsearch -u target.com -e sh,txt,htm,php,cgi,html,pl,bak,old -w wordlist.lst
```

### Wfuzz

```bash
wfuzz -c -v -u http://x.x.x.x/FUZZ -w worlist.lst --hc 404
```

### Rustbuster

```bash
rustbuster dir -u http://x.x.x.x/ -w wordlist.lst -S 404 -e php,txt -o rustbuster-medium.txt
```
[Github Rustbuster](https://github.com/phra/rustbuster)

## Parametros HTTP

### Arjun

```bash
arjun -u https://api.example.com/endpoint --get
```
[Github Arjun](https://github.com/s0md3v/Arjun)

### Ffuf

```bash
ffuf -u www.url.com/\?FUZZ=1 -w wordlist.lst
```

## VHosts

### Gobuster

```bash
gobuster vhost -u http://ejemplo.htb/ -w worlist.lst
```

### Rustbuster

```bash
rustbuster vhost -u http://x.x.x.x/ -w custom.txt -d ejemplo.htb -x 'redirect'
```
[Github Rustbuster](https://github.com/phra/rustbuster)


# Escaner y enumeracion

## Escaneando S.O.

### Ping (rudimentario)

```bash
ping -c 1 x.x.x.x
#TTL = 64 => Linux
#TTL = 128 => Windows
```

### Nmap

```bash
nmap -O x.x.x.x
```

## Escaneando WAFs

### Wafw00f

```bash
wafw00f www.url.com
```

### Nmap

```bash
nmap -p80,443 --script=http-waf-detect --script-args="http-waf-detect.aggro, http-waf-detect.detectBodyChanges"
nmap -p80,443 --script=http-waf-fingerprint --script-args="http-waf-fingerprint.intensive=1"
```

## Buscando metadatos online

### Nmap

```bash
nmap -p80,443 --script=http-exif-spider

#si tenemos error "Current http cache size exceeds max size"
nmap -p80,443 --script= http-exif-spider --script-args="http.max-cache-size=99999999"
```

### FOCA

[Github FOCA](https://github.com/ElevenPaths/FOCA)

## Escaneando SMB

### Nmap

```bash
nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse
```

### smbmap

```bash
smbmap -H host
smbmap -u user -p pass -H host
```

### enum4linux

```bash
enum4linux -U HOST #users
enum4linux -S HOST #enumera shares
enum4linux -P HOST #password policy
enum4linux -O HOST #info del SO
```

## Escaneando LDAP

puertos: 389, 636 (SSL), 3268, 3269 (SSL)

### Windapsearch

```bash
python windapsearch.py -u Administrator -p Pass123 -d dev.corp --dc-ip 10.10.10.19
```

[Github windapsearch](https://github.com/ropnop/windapsearch)

### ad-ldap-enum

SOLO Python2
```bash
python ad-ldap-enum.py -d dev.corp -l 10.10.10.19 -u Administrator -p Pass123
```

[Github ad-ldap-enum](https://github.com/CroweCybersecurity/ad-ldap-enum)

## Escaneando RPC

```bash
rpcinfo -p www.url.com
```

## Escaneando SNMP

### SNMPwalk

```bash
snmpwalk -c public -v1 IP
```

### snmpcheck

```bash
snmpcheck -t IP -c public
```

### onesixtyone

```bash
onesixtyone -c names -i hosts
```

### snmpenum

```bash
snmpenum -t IP
```

### Nmap

```bash
nmap -sV -p 161 --script=snmp-info IP
```

## Escaneando MSSQL

### Nmap

```bash
$nmap -p 1433 --script ms-sql-info,ms-sql-empty-password,ms-sql-xp-cmdshell,ms-sql-config,ms-sql-ntlm-info,ms-sql-tables,ms-sql-hasdbaccess,ms-sql-dac,ms-sql-dump-hashes --script-args mssql.instance-port=1433,mssql.username=sa,mssql.password=,mssql.instance-name=MSSQLSERVER $ip
```

## Escaneando RDP

### xfreerdp

```bash
xfreerdp /v:IP -sec-nla /u:""
```

## Git grabber

```bash
gitjacker www.url.com
```

## Escaner XSS

### XSStrike

```bash
xsstrike -u www.url.com/?id=
```

### Puff

```bash
puff -w xss.txt -u "http://url.com?id=FUZZ"
#si el WAF filtra el alert() podes usar puff() para reemplazar en el payload
```

### Pwnxss

```bash
pwnxss -u www.url.com
```

## Escaner CRLF

### CRLFuzz

```bash
crlfuzz -u www.url.com
```

### CRLFmap

```bash
$crlfmap scan --domains domains.txt --output results.txt
```

## Escaner CSRF / XSRF

```bash
xsrfprobe #suite
```

## Escaner SSL

```bash
sslscan https://www.url.com
```

## POP3

```bash
Telnet IP 110 #default port
USER username
PASS password
LIST #lista mensajes
RETR numMSG #muestra mensaje
QUIT
```

# Web scanners

## Nikto
## Wikto
## Nessus
## ZAP

## LFI

```bash
kadimus -u www.url.com/?pg=contact
```

```bash
lfisuite.py #framework scan and exploit
```