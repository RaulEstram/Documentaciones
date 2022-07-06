# Configuración de redes

El comando **ifconfig** significa “configuración de interfaz” (interface configuration) y se utiliza para mostrar información sobre la configuración de red.

```shell
$ ifconfig [OPCIONES] 
```

> **Note**
> El comando iwconfig es similar al comando ifconfig, pero se refiere a interfaces de redes inalámbricas (wireless).

El comando ifconfig también se puede utilizar para modificar temporalmente la configuración de red. Normalmente, estos cambios deben ser permanentes, por lo que raramente se usa el comando ifconfig para realizar dichos cambios.

El comando ping se utiliza para verificar la conectividad entre dos equipos. Para hacer esto, envía paquetes a otra máquina a través de la red. Que el remitente reciba una respuesta indica que es posible conectarse a esa máquina.

De forma predeterminada, el comando ping continuará enviando paquetes hasta que se introduzca el comando break (CTL +C) en la consola. Para limitar el número de pings que se envían, utilice la opción -c seguida del número de pings que desea enviar. El siguiente ejemplo muestra un ping limitado a 4 iteraciones usando -c 4.

```shell
$ ping -c 4 192.168.1.1
```
