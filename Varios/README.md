# Varios

* [Reversing](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#reversing)
* [BoF](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#BoF)
* [Malware Analysis](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#Malware)
* [Forense](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#Forense)
* [Programacion](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#Programacion)
* [Github](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#Github)
* [Esteganografia](https://github.com/HerculesRD/HerculesDocs/tree/main/Varios#Esteganografia)

## Wireshark

* [CheatSheet](https://github.com/HerculesRD/HerculesDocs/blob/main/Varios/Wireshark_Cheatsheet.md)

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





