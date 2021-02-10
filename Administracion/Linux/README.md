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
find / #ruta desde donde se busca (recursivo)
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

#### Which

```bash
```

### Grep

```bash
grep palabra file.txt  #busca la palabra dentro del archivo
grep -i #ignorar min y may
grep -r #recursivo
grep -w #solo match la palabra
grep -v #excluir en vez de grep
grep -x #matchear SOLO la linea
grep -l #solo muestra los ficheros que matcheo
grep -c #cuenta la cantidad de matchs
grep -C 2 #imprime las 2 lineas antes y despues del march
grep -n #muestra el numero de las lineas
grep -m2 #limita la salida en cantidad de lineas
```

### Permisos

#### chmod

```bash

```

#### chown

```bash
```

### Agregar usuarios

#### adduser

```bash
```

#### addgroup

```bash
```

#### usermod

```bash
```

### background jobs

```bash
&
bg
kill
fg
```

### Variables de entorno

#### bash

```bash
```

#### fish

```bash
```

## Port Knocking

```bash
```

## RegEx

```bash
```

## Comandos utiles (2)

### Formato texto

#### awk

#### sed

#### cut

#### tr

### echo

### Iteracion

#### watch

#### Crontab

### Formato archivos

#### xxd

#### gcc