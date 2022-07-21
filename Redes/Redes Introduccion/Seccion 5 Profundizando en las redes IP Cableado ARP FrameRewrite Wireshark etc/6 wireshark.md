# Wireshark

Wireshark es un analizador de protocolos utilizado para realizar análisis y solucionar problemas en redes de comunicaciones, para análisis de datos y protocolos, y como una herramienta didáctica.

Wireshark es software libre, y se ejecuta sobre la mayoría de sistemas operativos Unix y compatibles, incluyendo Linux, Solaris, FreeBSD, NetBSD, OpenBSD, Android, y macOS, así como en Microsoft Windows.

## Instalar Wireshark 

Wireshark lo utilizaremos para analizar paquetes, protocolos y muchas cosas es por esto que lo tenemos que tener instalado

## Windows

Vas a la pagina oficial de [wireshark](https://www.wireshark.org/) y [Descargas](https://www.wireshark.org/#download) el instalador como cualquier otro programa.

## Linux

Para instalar wireshark desde linux tenemos que usar los siguientes comandos:

```bash
$ sudo apt update
$ sudo apt upgrade
$ sudo apt install wireshark
```

En medio de la instalacion te pediran seleccionar "YES" o "NO", tendremos que **SELECCIONAR "YES"**

porteriormente tendremos que intresar los siguientes comandos:

```bash
$ sudo usermod -aG wireshark {tu usuario de linux}
$ sudo reboot
```

## Primeros pasos con Wireshark

Lo primero que veremos al abrir Wireshark sera algo similar a lo siguiente:

![Imagen30](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen30.png)

Lo que tiene Wireshark es que nos permite seleccionar la interfaz por donde vamos a capturar la trafico.

Tambien otra opcion que nos permite wireshark es agregar un filto en la parte de "usando este filtro: ".

Hay 2 tipos de filtros de wireshark:

* Filtros de Captura = Son los que agregamos antes de reazliar la captura de trafico y condiciona lo que capturamos
* Filtros de visualizacion = Son aquellos que agregamos posteriormente a realizar la captura de trafico y nos sirve para filtrar el trafico que nos interesa.

## Seleccionar una Interfaz 

Tendremos que seleccionar una interfaz en nuestro wireshark, en este caso sera la de nuestro internet o wifi, le damos doble clik o click derecho e iniciar captura.

Veremos algo similar a lo siguiente:

![Imagen31](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen31.png)

Posteriormente detendremos la captura de trafico con el boton rojo de la parte superior izquierda.

En este punto podemos seleccionar cualquier Trama o paquete que capturamos y podremos ver su informacion.

![Imagen32](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen32.png)

Dentro de la informacion podremos ver la informacion de la siguiente forma:

* Resumen de la trama/paquete
* Informacion de la capa 2
* Informacion de la capa 3
* Informacion de las capas superiores ...

Dependiendo del trafico mostrara mas informacion o menos.

### Aplicar Filtro y Visualizacion de Protocolo ARP

Tambien en la parte de "aplique un filtro de visualizacion" podemos poner algun filtro de visualizacion para filtrar las capturas de trafico, en este caso simplemente agregaremos ```arp``` y daremos enter.

Una vez hecho la anterior podremos ver el trafico capturado de protocolo ARP.

![Imagen33](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen33.png)

En este caso podemos ver estas 2 capturas ARP:

* Peticion ARP

![Imagen34](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen34.png)

Podemos ver que wireshark nos muestra en el protocolo Ethernet II:
* MAC destino
* MAC Origen
* Tipo que es 0x0806 que significa que es ARP

Por otro lado en Address Resolution Protocol podemos ver la informacion del protocolo ARP:

* Hardware Type = Ethernet
* Protocol Type = 0x0800, que es IPv4
* Hardware Address length = 6
* Protocol Address length = 4
* Operation Code = 1 que es de Peticion
* Sender Hardware Address = MAC Origen
* Sender Protocol Address = IP Origen
* Target Hardware Address = MAC destino que es 0000.0000.0000 ya que no conocemos el MAC destino
* Target Protocol Address = IP destino


* Respuesta ARP

![Imagen35](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen35.png)

Podemos ver que wireshark nos muestra en el protocolo Ethernet II:
* MAC destino
* MAC Origen
* Tipo que es 0x0806 que significa que es ARP

Por otro lado en Address Resolution Protocol podemos ver la informacion del protocolo ARP:

* Hardware Type = Ethernet
* Protocol Type = 0x0800, que es IPv4
* Hardware Address length = 6
* Protocol Address length = 4
* Operation Code = 2 que es de Respuesta
* Sender Hardware Address = MAC Origen
* Sender Protocol Address = IP Origen
* Target Hardware Address = MAC destino.
* Target Protocol Address = IP destino