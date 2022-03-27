# Tshark

```bash
$ Conocer los dispositivos de red
tshark -D 

$ tshark -r file.pcap --color
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

