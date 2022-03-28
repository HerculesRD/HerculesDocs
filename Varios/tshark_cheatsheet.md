# Tshark

```bash
Conocer los dispositivos de red
$ tshark -D 
Conectar
$ ipconfig eth0 promisc
$ tshark -i eth0

Cantidad de paquetes limitada
$ tshark -i eth0 -c 10

Leer y escribir en pcap files
$ tshark -i eth0 -c 10 -w file.pcap
$ tshark -r file.pcap

Verbose
$ tshark -r file.pcap -V

Con colorcito
$ tshark -r file.pcap --color
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
```

