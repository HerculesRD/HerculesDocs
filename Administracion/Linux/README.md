# Linux

* [Tools](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Linux#tools)
* [Comandos utiles (1)](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Linux#comandos-utiles-1)
* [Portknocking](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Linux#port-knocking)
* [REGEX](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Linux#regex)
* [Comandos Utiles (2)](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Linux#comandos-utiles-2)
* [Bash scripting](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Linux#tbash-scripting)
* [IPTables](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Linux#iptables)
* [Tips & Tricks](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Linux#tips-&-tricks)

## Explica comandos

* [explainShell](https://explainshell.com/)
* [shellHow](https://www.shell.how/)

## Tools

* [BatCat](https://github.com/sharkdp/bat)
* [Exa](https://github.com/ogham/exa)

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
which bash #Cual es el path absoluto del binario al que llamas de manera relativa
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
chmod 0777 archivo.txt (-rwxrwxrwx)
chmod o=rwx archivo.txt (-------rwx)
chmod a+r archivo.txt (-r--r--r--)
chmod -R #que mire tambien los subdirectorios de la ruta
chmod -v #muestra cada fichero procesado
chmod -c #muestra cada fichero procesado que tuvo cambios
```

#### chown

```bash
chown user:group file.txt
-R -v -c #igual que chmod
```

### Agregar usuarios

#### adduser

```bash
adduser usuario
passwd usuario
```

#### addgroup

```bash
addgroup grupo
```

#### usermod

```bash
usermod -d /home/path usuario #le das un home 
usermod -s /bin/sh usuario #modificar la shell
```

### background jobs

```bash
nmap IP -oN salida.txt & #hace la tarea en el background

bg

usermod -d /home/path usuario #le das un home 
usermod -s /bin/sh usuario #modificar la shell

fg
```

### Variables de entorno

#### bash

```bash
export variable_de_entorno=valor
```

#### fish

```bash
set -x variable de entorno valor
```

## Port Knocking

```bash
knock IP port1 port2 port3 && ssh -i id_rsa IP
```

## RegEx

```bash
. #un caracter
? #el anterior caracter aparece 0 o 1 vez
* #el anterior caracter aparece 0 o mas veces
+ #el anterior caracter aparece 1 o mas veces
{n} #el anterior caracter aparece exactamente n veces
{n,m} #el anterior caracter aparece al menos n veces y no mas de m veces
{n,} #aparece n o mas veces
[asd] #el caracter es uno incluido entre los corchetes
[^asd] #el caracter NO es uno de los incluidos entre los corchetes
[a-d] #el - funciona estableciendo un rango
() #agrupa
| #or
^ #Primer caracter de la linea
$ #ultimo caracter de la linea
\< #al empezar la palabra
\> #al terminar la palabra
a-z A-Z #alfabeto
\d #digitos del 0 al 9
\D #cualquier no digito
#escapes
\. 
\?
\s #espacio
\S #sin espacios
\i #case insensitive
```

## Comandos utiles (2)

### Formato texto

#### awk

```bash
awk patron {accion} # sintaxis

awk '{print}' file.txt #imprimir todas las lineas del fichero con saltos de linea
awk '/admin/ {print}' file.txt #print lineas que matchea con "admin" (podes usar REGEX)
awk '{! /admin/ print}' file.txt #print lineas que NO matcheen con "admin"
awk '{print $5,$4}' file.txt #print columna 5 y 4 en ese orden
awk '{print $1 ":" $4}' file.txt #print colum 1 y 4 separadas por :
awk '{print $NF}' file.txt #imprimir ultima columna de cada linea
awk '{print NR,$0}' file.txt #print las lineas numeradas
awk -F ';' '{print $3}' file.txt #print tercera columna, delimitar con ;

awk '{length}' file.txt #largo del texto
awk '{tolower}' file.txt #convierte en minusculas
awk '{toupper}' file.txt #convierte todo en mayusc
awk '{printf}' file.txt #imprime sin saltos de linea
```

#### sed

```bash
sed 'operacion' file.txt #sintaxis

sed 's/chau/hola/g' file.txt #reemplazar chau por hola cada cez en el texto
#podemos usar /gi en vez de /g para no tomar en cuenta min o may
sed 's/\s+/ /g' file.txt #reempazar 2 o mas espacios por uno solo
sed 's/^/*/g' file.txt #poner un * al principio de cada linea
sed '2,7 d' file.txt > file2.txt #eliminar las lineas 2 a 7

sed '/AAA/!d; /BBB/!d; /CCC/!d' file.txt #buscar AAA, BBB o CCC
sed '/AAA.*BBB.*CCC/!d' file.txt #buscar AAA Y BBB Y CCC

```

#### cut

```bash
$cut -d ':' -f 3 abc.txt #muestra la tercer cadena separando por :
#por defecto usa el tabulador como separador
```

#### tr

```bash
$tr 'B' 'V' < file.txt > file2.txt #reemplaza B por V y lo guarda en file2
$tr [:upper:] [:lower:] < file.txt > file2.txt #reemplaza mayus por min
$tr -d '0-9' < file.txt > file2.txt #borrar todos los numeros del fichero
```

### echo

```bash
echo -n #sin salto de linea

echo $0 #devuelve el codigo de estado, que es el valor final del ultimo retorno.
#0 para correcto, 1 para incorrecto
```

### Iteracion

#### watch

```bash
#repite un comando cada cierto tiempo
$watch -n 1 'ls -la' #cada 1 segundo
```

#### Crontab

```bash
crontab -e #para editar el archivo actual
1 2 3 4 5 ls

#1 minuto
#2 hora
#3 dia del mes
#4 mes
#5 dia de la semana (0 = domingo, 0-6)

crontab -l #listamos las tareas existentes

crontab -d #borramos el crontab
```

### Formato archivos

#### xxd (volcado hexa)

```bash
xxd foto.jpg 
```

#### gcc (compilador C)

```bash
gcc -o salida entrada.c
```

#### g++ (compilador C++)

```bash
g++ -o salida entrada.cpp
```

## Bash scripting

### Inicio

```bash
#!/bin/bash
```

### Funciones

#### Interrupcion CTRL+C

```bash
function ctrl_c {
	echo -e "\n\n[*]Exiting...\n"
	exit 0
}

trap ctrl_c INT
```

### Control de tiempo

```bash
timeout 1 bash -c "echo 'Hola'"
```

### Logica

#### usar && como IF

```bash
for i in $(seq 1 10) do:
	cat file | grep $i >/dev/null && echo "Se encontro el numero $i"
done
```

### Cursor

```bash
tput civis #oculta el cursor
tput cnorm #muestra el cursor
```

### Color

```bash
YELLOW='\033[1;33m'
NC='\033[0m'
echo -e "${YELLOW}Color${NC}" #NC es para NO COLOR
```

### Parametros

#### getopts

```bash
getopts ":H:l" opt

## Los ":" a la derecha indican si necesita argumento

## H: 	requiere argumento
## l 	no requiere argumento

####ejemplo
while getopts ":H:l" opt; do
        case "${opt}" in

                H)
                        #hace algo
                        ;;

                l)
                        #hace algo
                        ;;

                *)
                        #hace esto por default
                        ;;

        esac
done
```

#### obteniendo un argumento de una opcion

```bash
while getopts ":H:" opt; do
        case "${opt}" in

                H)
                        var=${OPTARG}
                        ;;
## etc
```

#### simple

```bash
# Para comprobar si la cantidad de argumentos es 0
if [ $# -eq 0 ]; then

#Saber si el primer argumento es igual a 0
if [ $1 -eq 0 ]; then

if [ ${10} -eq 0 ]; then #para luego del 9no argumento se cierran asi

#todos los argumentos en un solo string
echo $*

```

### Datos del script

#### nombre del script

```bash
echo el nombre del script es $0
```

#### PID del script

```bash
echo este es el PID del script, $$
```

#### Ultimo valor de retorno (return code)

```bash
echo el ultimo ret code fue $?
```

## IPTables

Lo termine pasando a otro archivo porque era muy largo. Hay que segmentar.
[IPTables](https://github.com/HerculesRD/HerculesDocs/tree/main/Administracion/Linux/IPTables)

## Tips & Tricks

#### Llamar al ultimo argumento del comando anterior

```bash
ls -l ../	#comando ejemplo
ls -l !$	#mismo resultado 
ls -l [alt + .]	#mismo resultado
```
