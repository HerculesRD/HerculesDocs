# Tshark

```bash
Conocer los dispositivos de red
$ tshark -D 
Conectar
$ ipconfig eth0 promisc
$ tshark -i eth0 -p

Cantidad de paquetes limitada
$ tshark -i eth0 -c 10

Leer y escribir en pcap files
$ tshark -i eth0 -c 10 -w file.pcap
$ tshark -r file.pcap

Verbose
$ tshark -r file.pcap -V

Con colorcito
$ tshark -r file.pcap --color

Capturar de un puerto en particular
$ tshark -i eth0 -c 5 -f "tcp port 80"

Display filter (como con la GUI de Wireshark)
$ tshark -i eth0 -c 5 -f "tcp port 80" -Y 'http.request.method == "GET" '
```

Formatos de salida
```bash
Conocer las opciones
$ tshark -T x

elegir una
$ tshark -r file.pcap -T text
```

Salida a HTML (desde pdml)
```bash
$ tshark -r file.pcap -T pdml > packets.xml
$ xsltproc /usr/share/wireshark/pdml2html.xsl packets.xml > packets.html
$ firefox packets.html &
```

Estadisticas
```bash
conocer todas las formas de analisis
$ tshark -z help

estadistica de protocolos
$ tshark -r file.pcap -z io,phs

arbol de distribucion de paquetes
$ tshark -r file.pcap -z http,tree -q

Analisis de conversacion
$ tshark -r file.pcap -z conv,wlan -q | head

Modo experto
$ tshark -r file.pcap -z expert -q | head
```

autostop (frena el analisis cuando se cumple una condicion)
```bash
Duracion en segundos
$ tshark -i eth0 -a duration:10

Tamaño en Kb
$ tshark -i eth0 -a filesize:1
```

Reporte
```bash
opciones de reporte
$ tshark -G help

opciones de columnas
$ tshark -G column-formats

plugins
$ tshark -G plugins

carpetas
$ tshark -G folders
```


