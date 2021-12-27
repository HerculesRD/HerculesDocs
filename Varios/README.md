# Varios

* [Reversing](https://github.com/HerculesRD/HerculesDocs/Varios#Reversing)
* [BoF](https://github.com/HerculesRD/HerculesDocs/Varios#BoF)
* [Malware Analysis](https://github.com/HerculesRD/HerculesDocs/Varios#Malware)
* [Forense](https://github.com/HerculesRD/HerculesDocs/Varios#Forense)
* [Programacion](https://github.com/HerculesRD/HerculesDocs/Varios#Programacion)
* [Github](https://github.com/HerculesRD/HerculesDocs/Varios#Github)
* [Esteganografia](https://github.com/HerculesRD/HerculesDocs/Varios#Esteganografia)


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

### Malware DDBB

* [abuse bazaar](https://bazaar.abuse.ch/browse/)

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
## Github
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





