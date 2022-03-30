# Varios

* [Analisis de red](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#analisis-de-red)
* [Reversing](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#reversing)
* [BoF](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#BoF)
* [Malware Analysis](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#Malware)
* [Forense](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#Forense)
* [Programacion](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#Programacion)
* [Docker](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#Docker)
* [Github](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#Github)
* [Esteganografia](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#Esteganografia)

## Analisis de red

* [Wireshark CheatSheet](https://github.com/HerculesRD/HerculesDocs/blob/main/Varios/Wireshark_Cheatsheet.md)
* [TShark CheatSheet](https://github.com/HerculesRD/HerculesDocs/blob/main/Varios/tshark_cheatsheet.md)

## Reversing

### Radare2

```bash
r2 -d file -A #debug y analisis del codigo
```

### Ghidra

## BoF

### Shellcoding

#### Database

[shell-storm](http://shell-storm.org/shellcode/)

### Hex editor

```bash
./ImHex
```

## Malware 

### Terminal Escape Injection

#### Linux

```bash
#!/bin/bash

echo "Evil!!!"
exit 0
^[[2Aecho "Instalando script..."
```

#### Windows

Para leer, con notepad. Las terminales no son confiables para leer
```powershell
@echo off

echo evill!

^[[2Aecho instalando script...
```

### Blacklists

* [Abuse URLs maliciosas](https://urlhaus.abuse.ch/browse/)
* [Abuse SSL cert Blacklist](https://sslbl.abuse.ch/blacklist/)
* [Abuse IP Blacklist](https://feodotracker.abuse.ch/blocklist/)

### Analisis Estatico

```bash
pdfid file.pdf #portable pdf analysis
```

* [virustotal](virustotal.com)
* PE Explorer
* Resource hacker
* PE View
* PEID
* Dependency Walker
* Hashtab
* Strings

### Analisis Dinamico

* IDA PRO
* Win DBG

## Forense

### Obteniendo Memoria

* FTKImager
* Redline
* Dumpit
* win32dd.exe / win64.exe

### Analizando memoria

* Volatility

## Programacion

* [Shell una linea](https://rosettacode.org/wiki/Shell_one-liner)

### Python

Ejecucion de comandos de OS
```python
os.system("ls")
os.popen("ls").read()
os.execl("/bin/ls","")
os.execlp("ls","")
os.execv("/bin/ls",[''])
os.execvp("/bin/ls",[""])
subprocess.call("ls")
    subprocess.call("ls|cat",shell=False) => Fail
    subprocess.call("ls|cat",shell=True) => Correct
eval("__import__('os').system('ls')")
exec("__import__('os').system('ls')")
commands.getoutput('ls')
```

Tshark en python

$ pip3 install pyshark
```python
# Live capture
import pysgark
capture = pyshark.LiveCapture(interface=='eth0')
capture.sniff(timeout=5)
capture

# Representar lo capturado
capture[1].pretty_print()

# Largo del paquete
pkt.layers
pkt.eth.src
pkt.eth.dst
pkt.eth.type

# Propiedades IP
dir (pkt,ip)
pkt.ip.src
pkt.ip.dst
pkt.ip.pretty_print()
```

## Docker

```bash
# Docker file to image
docker build -t <tagname> .

# Descargando docker file
# ultima version
docker pull <container name>
# Version especifica
docker pull <container name>:<verion>
```

Corriendo container
```bash
# listando imagenes de docker
docker images 

# Corriendo el container
docker run -it <dockername>

# Eliminando container
docker rmi <imageID> -f

# Listar instancias de Docker
docker ps

# Actualizar Docker cuando alteramos containers
docker update
```

Corriendo Docker con puertos abiertos
```bash
docker run --rm -it -p <port on docker container>:<port on docker host> -p <port start>-<port end>:<port start>-<port end> <imageName>
# single port 
docker run --rm -it -p 21:21 <imageName>
# continuous multiple ports
docker run --rm -it -p 21:21 -p 4559-4564:4559-4564 <imageName>
```

## Github

* [Profile README generator](https://rahuldkjain.github.io/gh-profile-readme-generator/)

## Esteganografia

```bash
strings file
```

```bash
steghide extract -sF file.jpg
```

```bash
zsteg file.png
```

```bash
exiftool file
```

```bash
stegoveritas file
```

```bash
stegcracker file
```

```bash
binwalk -h
```





