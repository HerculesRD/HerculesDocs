# Administracion

1. Linux
	* Tools
	* Comandos utiles (1)
	* Portknocking
	* REGEX
	* Comandos Utiles (2)
	* IPTables
1. Windows

# Linux

## Tools

### Batcat | cat con esteroides

[Github Link](https://github.com/sharkdp/bat)

## Comandos utiles (1)

### Ocultar errores

```bash
2>/dev/null
#ejemplo
cd directorioNoExistente 2>/dev/null
```

### Buscar archivos
#### Find
```bash
$ find / #ruta desde donde se busca (recursivo)
find / -name nombreFichero
find / -type f #f=file, d=directorio
find / -perm 660 #permisos exactos
find / -perm u=r #otra notacion
find / -perm /660 #al menos uno de estos permisos es verdad
find / -perm -u=r #AL MENOS este permiso
find / -size +100c #MAS de 100 bytes. Puede usarse "-", k (kb) o m (mb)
find / -user owner
```
#### Locate
```bash
sudo updatedb #quizas necesitemos actualizar la db antes
locate nombreFichero
```

