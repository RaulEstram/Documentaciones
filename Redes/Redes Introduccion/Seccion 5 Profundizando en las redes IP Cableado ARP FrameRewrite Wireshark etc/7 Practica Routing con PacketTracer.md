# Practica: Routing con PacketTracer.

Para esta practica tenemos las siguientes Redes interconectadas por un Router:

![Imagen36](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen36.png)

Lo que tiene esta practica es que ya tiene configuradas las IPs y MACs de los equipos finales, por otro lado los Switches practicamente no se les a movido nada.

Lo unico que vamos a configurar es el Router el cual por defecto tiene las interfaces DOWN o dehabilitadas y lo que tenemos que haces es habilitarlas y configurarlas.

> **Note** Podemos encontrar esta practica en la carpeta "Programas con el nombre de "5 7 Practica Routing Inicio.pkt"

## Configuracion de Router

## 1° habilitar las interfaces

Tendremos que ir al CLI del Router, si nos pregunta "Would you like to enter the initial configuration dialog? [yes/no]:" le daremos que NO.

porteriormente habilitaremos las interfaces que tenemos conectadas para esto tenemos que ir al submodo de configuracion global de las interfaces y habilitarlas con ```not shutdown```.

En este caso el codigo es:

```terminal
Router>enable
Router#conf t
Router(config)# interface gigabitEthernet 0/0
Router(config-if)# no shutdown
```

Con el codigo anterior entramos al submodo de interfaz de la configuracion global para poder levantar la interface a la que esta conectado una red, realizaremos practicamente lo mismo para el otro gigabitEthernet que es el 0/1.

El codigo de nuestro CLI es similar al siguiente:

* gigabitEthernet 0/0

![Imagen37](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen37.png)

* gigabitEthernet 0/1 

![Imagen38](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen38.png)

Por lo tanto nuestras Red nos quedara de la siguiente manera donde veremos que las interfaces ya no estan DOWN ahora se encuentran UP.

![Imagen39](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen39.png)

> **Note** Podemos ver un pequeño resumen de la configuracion de las interfaces usando **```show ip interface brief```** o uno mas largo con **```show interfaces```** desde el modo privilegiado del Router

---

### 2° Configurar las Interfaces del Router

En este punto solamente hemos levantado o habilitado las interfaces del Router, si intentamos un **ping** de un equipo final a otro equipo final en diferentes redes, no habra ninguna respuesta, y esto se debe a que no hemos configurado las interfaces del Router.

**Para configurar las Interfaces del Router** tenemos que **ir al modo de configuracion global** y posteriormente al **submodo de configuracion de cada interfaz**, una vez en este modo usaremos el comando ```ip address {ip} {subnet mask}``` donde le definiremos la red correspondiente para esta interfaz.

Los comandos para realizar esta configuracion serian:

```terminal
Router>enable
Router#configure terminal 
Router(config)#interface gigabitEthernet 0/1
Router(config-if)#ip address 10.2.2.1 255.255.255.0
```

![Imagen40](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen40.png)

> **Note** "No importa" que IP le pasemo, simplemente que esta IP tiene que ser una IP de host de nuestra Red, no puede ser la IP de Broadcast ni la de Red. Generalmente se apartan las primeras o las ultimas IPs de host de una Red para los equipos de red dentro de cada Red IP. 


Una vez configuradas las dos interfaces podemos vizualizar la tabla de Rutas desde el modo de configuracion con el comando ```show ip route```

## 3° Configurar el Default Gateway

En este punto ya tenemos configurado el Router, pero para que un equipo final de una Red IP se pueda comunicar con otro equipo final de otra Red IP, es necesario configurar su Defaul Gateway para que pueda enviar cosas fuera de su red.

El Default Gateway de los equipos finales para que puedan enviar cosas fuera de su red sera la interfaz del Router que da a esta Red (El IP que se le dio a la interfaz cuando se configuro el Router).

El Gateway se configura desde Config>Global>Settings>Default G
ateway de cada equipo final

## 4° ping

Una vez hecho los 3 pasos anteriores podemos enviar pings de un equipo final a otro equipo final sin ningun problema y de esta manera comprobar la conectividad de nuestras redes.


> **Note** Podemos encontrar esta practica finalizada en la carpeta "Programas con el nombre de "5 7 Practica Routing Final.pkt"