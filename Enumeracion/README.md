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
```

## Versiones
## Salida
## Salteando escudos
## Scripts
## Opciones Adicionales

```bash
nmap 192.168.1.2 --traceroute
nmap 192.168.1.2 --system-dns #usar el dns del sistema
nmap 192.168.1.2 --dns-servers <dns-server> #usar un dns especifico
```

# Amass

# Descubrimiento de dir & files

# Escaneres


