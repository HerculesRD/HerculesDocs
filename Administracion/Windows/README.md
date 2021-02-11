# Windows

## Comandos utiles

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

### Ocultar errores

```powershell
Get-Content /etc/passwd -ErrorAction SilentlyContinue
```