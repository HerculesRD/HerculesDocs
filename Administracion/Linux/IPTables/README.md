# IPTables

## Mostrar reglas

### Mostrar todas las reglas

```bash
sudo iptables -n -L -v
```

## Manejo de reglas

### Agregar

```bash
sudo iptables -A
```

### Agregar en un lugar especifico de la cadena

```bash
sudo iptables -I INPUT 2 #segundo lugar de la chain
```

### Borrar

```bash
sudo iptables -D
```

### Reemplazar

```bash
sudo iptables -R
```

### Borrar todas las reglas de una cadena

```bash
sudo iptables -F
```

### Pone a 0 todos los contadores de una cadena

```bash
sudo iptables -Z
```

### Politicas por defecto

```bash
sudo iptables -P
```

## Hooks

### Prerouting (antes de entrar a la pila de red del kernel)

```bash
sudo iptables -A INPUT
```

### Ingreso de paquete

```bash
sudo iptables -A INPUT
```

### Luego de haber sido routeado y destinado a otro host

```bash
sudo iptables -A FORWARD
``` 

### Salida de paquete (antes de entrar a la pila de red del kernel)

```bash
sudo iptables -A OUTPUT
```

### Postrouting (justo antes de salir a la red)

```bash
sudo iptables -A POSTROUTING
````

## Condiciones principales

### Protocolos

```bash
sudo iptables -A INPUT -p tcp
#tcp, udp, udplite, icmp, icmpv6,esp, ah, sctp, mh o "all".
```

### IP de origen

```bash
sudo iptables -A INPUT -s x.x.x.x
```

### IP destino

```bash
sudo iptables -A OUTPUT -d x.x.x.x
```

### Interfaz de origen

```bash
sudo iptables -A OUTPUT -i eth0
```

### Interfaz de destino

```bash
sudo iptables -A INPUT -o eth0
```

### Puerto de destino

```bash
sudo iptables -A INPUT --dport 21
```

### Puerto de origen

```bash
sudo iptables -A OUTPUT --sport 21
```

## Accion

### Descarta paquete

```bash
sudo iptables -A Input -p tcp --dport 21 -j DROP
```

### Rechaza paquete (responde)

```bash
sudo iptables -A Input -p tcp --dport 21 -j REJECT
```

### Acepta paquetes

```bash
sudo iptables -A Input -p tcp --dport 21 -j ACCEPT
```

### Modifico la IP de destino (Prerouting)

```bash
sudo iptables -A Input -p tcp --dport 21 -j DNAT -to x.x.x.x
```

### Modifico la IP de origen (Postrouting)

```bash
sudo iptables -A Input -p tcp --dport 21 -j SNAT -to x.x.x.x
```

