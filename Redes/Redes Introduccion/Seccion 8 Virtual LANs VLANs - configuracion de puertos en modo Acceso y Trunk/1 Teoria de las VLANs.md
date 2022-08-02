# Teoria de las VLANs


Las Virtual LANs o VLANs son una tecnologia que aplica a equipos de capa 2 como lo son los switches, pero antes de ver que son o para que funcionan tenemos que ver algunas cosas como son el Dominio de Broadcast.

## Dominio de Broadcast

El dominio de Broadcast hace referencia a todo el conjunto de equipos que sean susceptibles de recibir una Trama del tipo Broadcast cuando esta sea enviada.

Si tenemos 10 equipos conectados a un Switch, esos 10 equipos serian el Dominio de Broadcast.

Si tuvieramos 3 Switches interconectados con 10 equipos por Switch, los 30 equipos que estan conectados a los 3 Switches serian el Dominio de Broadcast.

Por lo tanto, mientas mas grande el Dominio de Broadcast, mas trafico inutil se genera gracias a las peticiones ARP y por lo tanto **mientras mas grande el Dominio de Broadcast menor eficiente sera la red.**

Gracias a la problematica con los Dominios de Broadcast grandes, sera muy util, tanto al momento de diseñar una nueva Red o para Redes ya existentes el **Segmentar los dominios de Broadcast.**

Una forma se segmentar los dominios de Broadcast es usando Routers ya que estos al recibir una trama de tipo Broadcast no lo reenvia directamente como lo haria un Switch, pero otra **forma de sergmentar los Dominios de Broadcast es usando las Virtaul LANs.**

## Virtual LANs o VLANs

De forma conceptual consiste en que gracias a las VLANs, con un solo Switch podemos definir diferentes LANs Virtuales y asociar los puertos a una VLAN o a otra en funcion a nuestras necesidades.

![Imagen49](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen49.png)

Tenemos un solo Switch pero a nivel logico es como tener varios Switches no conectados entre si, lo que permite aislar el trafico entre diferentes VLANs como el trafico Broadcast, Multicast o Unicast.

## Motivos para utilizar VLANs

Hay diferentes motivos por las que podemos usar las VLANs, como son:

* Coste: evita comprar nuevos Switches y Routers para aislar el trafico.
* Limita el numero de equipos que reciben los Broadcast.
* Limita el numero de equipos que reciben Flooding.
    * Reduce el uso de CPU de los equipos
        * Equipos de red
        * Equipos Finales
    * Incrementa la Seguridad, nos permite aislar diferentes Redes.
* Agrupar los equipos de forma Logica y no Fisica.


Imaginemos que tenemos el siguiente escenario.

![Imagen50](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen50.png)

Los que nos permite las VLANs en este tipo de escenarios es que exista comunicacion entre la VLAN 1 de la planta 1 con la VLAN 1 de la planta 3. En estos casos donde tenemos VLANs repartidas en diferentes Switches y con comunicacion entre estas se hace referencia a ello como que una VLAN esta extendida a lo largo de la red (a lo largo de varios Switches).

Es aqui donde nos preguntamos ¿ Como hacemos que el trafico de la VLAN-1 en la Planta 1 llegue a la VLAN-1 en la Planta 3 ? pues para realizar esta tarea surgieron los enlaces de tipo Trunk.

## Enlace Trunk - Trunking

El enclace Trunk es un unico enlace entre Switches que transporta todas la VLANs que queremos, el protocolo que define esto es el 802.1 Q o dot1Q.

Esta tecnologia lo que hace es que añadimos una pequeña cabecera en la trama ethernet para diferenciar las tramas de cada VLAN

![Imagen51](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen51.png)

Para realizar esto tenemos que configurar los puertos en modo Access para los equipos finales y en modo Trunk para el enlace Trunk. Aunque hay casos donde esto puede variar ya que en realidad el Modo Access solamente permite el trafico de una sola VLAN mientras que el Modo Trunk permite el trafico de varios VLANs.


### VLAN Nativa

Cada Trunk debe tener definida una VLAN Nativa a la cual:

* No se añade cabecera 802.1Q a los paquetes que se envian por esta VLAN
* Cuando un Switch, recibe por un Trunk un paquete sin cabecera 802.1Q considera que el paquete forma parte de la VLAN Nativa.

> **Note** Debe configurarse la misma en ambos extremos 

## Diseño de las VLANs

Hay casos donde vamos a querer que una VLAN se comunique con otra VLAN, para realizar esto podemos utilizar el Routing, pero para esto es importante asignar redes distintas a cada VLAN.