# Windows
* [Tools](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#tools)
* [Comandos utiles](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#comandos-utiles)
* [Permisos](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#permisos)
* [Manejo de procesos y servicios](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#manejo-de-procesos-y-servicios)
* [Logs](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#logs)
* [Informacion de sistema](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#informacion-de-sistema)
* [RDP](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#rdp)
* [Redes](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#redes)
* [SMB](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Windows#SMB)
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

* Get privs
```cmd
whoami /priv
```

#### powershell

```powershell
$env:username
[System.Security.Principal.WindowsIdentity]::GetCurrent().Name
```

* Get SID
```powershell
([System.Security.Principal.WindowsIdentity]::GetCurrent()).User.Value
```

* Tengo privs de admin?
```powershell
If (([Security.Principal.WindowsPrincipal] [Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole] "Administrator")) { echo "yes"; } else { echo "no"; }
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

### Habilitar RDP

```powershell
(Get-WmiObject -Class "Win32_TerminalServiceSetting" -Namespace root\cimv2\terminalservices).SetAllowTsConnections(1)
```

### Deshabilitar NLA

```powershell
(Get-WmiObject -class "Win32_TSGeneralSetting" -Namespace root\cimv2\terminalservices -Filter "TerminalName='RDP-tcp'").SetUserAuthenticationRequired(0)
```

### Permitir RDP en el firewall

```powershell
Get-NetFirewallRule -DisplayGroup "Remote Desktop" | Set-NetFirewallRule -Enabled True
```

## Redes

### Setear MAC Adress

```powershell
Set-NetAdapter -Name "Ethernet0" -MacAddress "00-01-18-57-1B-0D"
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

## SMB

### Habilitar con acceso anonimo

```powershell
new-item "c:\users\public\share" -itemtype directory
New-SmbShare -Name "sharedir" -Path "C:\users\public\share" -FullAccess "Everyone","Guests","Anonymous Logon"
```

### Parar SMB

```powershell
Remove-SmbShare -Name "sharedir" -Force
```

## CMDLets

### filtrado

```powershell
Get-Service | Where-Object ($_.Status -eq "Stopped")
```