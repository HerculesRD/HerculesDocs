# Enumeracion

1. Nmap
	* Objetivos
	* Descubrimiento
	* Puertos
	* Versiones
	* Salida
	* Salteando escudos
	* Scripts
	* Opciones
2. Amass
3. Descubrimiento de dir & files
	* Tips & Tricks
	* Fuzzers
	* Parametros HTTP
	* VHosts
4. Escaneres
	* Web Scanners
	* Escaneando S.O.
	* Escaneando WAFs
	* Buscando metadatos online
	* Escaneando SMB
	* Escaneando LDAP
	* Escaneando RPC
	* Escaneando SNMP
	* Escaneando MSSQL
	* Escaneando RDP
	* Git grabber
	* Escaner XSS
	* Escaner CRLF
	* Escaner CSRF
	* Escaner SSL

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
## Salteando escudos
## Scripts
## Opciones Adicionales

```bash
nmap 192.168.1.2 --traceroute
nmap 192.168.1.2 --system-dns #usar el dns del sistema
nmap 192.168.1.2 --dns-servers <dns-server> #usar un dns especifico
nmap 192.168.1.2 -ddddddddddd #debugging
```

# Amass

# Descubrimiento de dir & files

# Escaneres


