# Windows
* [Tools](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#tools)
* [Comandos utiles](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#comandos-utiles)
* [Permisos](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#permisos)
* [Manejo de procesos y servicios](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#manejo-de-procesos-y-servicios)
* [Logs](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#logs)
* [Informacion de sistema](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#informacion-de-sistema)
* [RDP](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#rdp)
* [Firmar certificado](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#firmar-certificado)
* [CMDLets](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#cmdlets)

## Tools

### Monitor de recursos

[Process Hacker](https://processhacker.sourceforge.io/)

## Comandos utiles

### HELP!

#### Que es esto

```powershell
Get-Help Get-Process
```

#### Mostrar los diferentes comandos disponibles

```powershell
Get-Command *-service*
```

### whoami

#### cmd

```cmd
whoami
echo %username%
```

#### powershell

```powershell
$env:username
[System.Security.Principal.WindowsIdentity]::GetCurrent().Name
```

### Directorios y archivos

#### ls

```powershell
Get-ChildItem
```

#### cat

```cmd
type file.txt
```

```powershell
Get-Content <file>
```

#### move 

```powershell
Move-Item <file.org> <file.mov>
```

#### copy

```powershell
Copy-Item <file.org> <file.cpy>
```

#### delete

```powershell
Remove-Item <file>
```

```powershell
Clear-Content file.txt #conserva el archivo pero borra lo de adentro
```

#### Busqueda de archivos

```cmd
findstr /spin "string" *.* 
```

### Ocultar errores

```powershell
Get-Content /etc/passwd -ErrorAction SilentlyContinue
```

## Permisos

### Politica de ejecucion del usuario

```powershell
#Que scripts podemos ejecutar
Get-ExecutionPolicy
#Niveles: Restricted (solo comandos) - All signed - Remote signed (signed+local script)
# - Unrestricted

Set-ExecutionPolicy Unrestricted
```

## Manejo de procesos y servicios

### Procesos

#### Mostrar Procesos

```powershell
Get-Process
```

#### Parar procesos

```powershell
Stop-Process note*
```

### Servicios

#### Mostrar Servicios

```powershell
Get-Service
```

## Logs

### Logs de sistema

```powershell
Get-EventLog -Log "Application"
#En vez de log tambien tenemos:
#-Verbose
#-Debug
#-ErrorAction
#-ErrorVariable
#-WarningAction
#-WarningVariable
#-OutBuffer
#-OutVariable

Get-EventLog -LogName System -After "DD/MM/YYYY" -EntryType Error
```

### Terminal log (solo de esa sesion)

```powershell
Clear-History -Command *help* #podemos elegir si todos o el historial de ciertos comandos
```

## Informacion de sistema

### Sysinfo

```cmd
systeminfo
hostname
whoami /all
```

### Usuarios y grupos

#### Local

```cmd
net users
net localgroups
net localgroups Administrators
net user hax0r
```

### Conexiones de red

```cmd
ipconfig /all
route print
arp -A
netstat -ano
```

#### domain

```cmd
net user hax0r /domain
net group Administrators /domain
```

### Dispositivos

#### USB Conectados

```powershell
Get-ItemProperty -ea 0 hklm:\system\currentcontrolset\enum\usbstor\*\* | select FriendlyName, PSChildName	
```

## RDP

### Conexion

```cmd
$xfreerdp /u:user /g:grupo /p:password /v:IP
```

## Firmar certificado

### Localmente

```powershell
$cert=Get-ChildItem -Path Cert:\CurrentUser\My -CodeSigningCert
Set-AuthenticodeSignature -FilePath script.ps1 -Certificate $cert
```

### Firmar con root authority

```powershell
Set-AuthenticodeSignature -FilePath c:\scripts\script.ps1 -Certificate $cert -IncludeChain All -TimestampServer "http://timestamp.fabrikam.com/scripts/timstamper.dll"
```

## CMDLets

### filtrado

```powershell
Get-Service | Where-Object ($_.Status -eq "Stopped")
```