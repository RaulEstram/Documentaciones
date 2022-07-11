# Redes Half Duplex: HUBs, Colisiones y el Protocolo CSMA/CD

El equipo estrella que nos encontramos en la capa 2 es el **Switch** y nos dara las funciones de acceso a la red, es decir, es el equipo al que le conectaremos los **equipos finales** y otros equipos como Routers.

## HUBs y Colisiones

Los HUBs ya no se utilizan pero formaron parte de la red por muchos años.

Los HUBs ofrece acceso a la red e Interconexion entre equipo.

Cuando el HUB recibe una trama, la reenvia por todas las interfaces que tiene menos por la interfaz por la cual la ha recibido.

Los HUBs tienen un inconveniente y es que NO podian enviar y recibir a la vez, esto se debe a que Repiten la señal que les entra por un puerto, reenviandola a todos los otros puertos y esto es lo unico que hace ya que no entiende de direcciones de capa 2 y es por esto que se considera como un equipo de Capa 1, como si fuera un cable para verlo de una forma sencilla.

Teniendo en cuenta lo anterior, ¿que pasa si 2 equipos enviar informacion al mismo tiempo? pues que habra un **colision**, es decir, que **la informacion de ambas tramas colisionara al intentar viajar a la vez por el mismo medio y por lo tanto perderemos la informacion**, por lo que no podemos enviar y recibir informacion a la vez, para evitar las colisiones.

Este tipo de redes se denomina como Half Duplex y para estas redes se tiene que seguir un protocolo donde:
* Primero escuchas antes de enviar
* Si alguien esta enviando datos --> esperamos 
* Cuando esta libre --> enviamos 

por lo tanto nunca se enviara y se recibira a la vez, pero siguiendo este protocolo minimisamos las colisiones, pero nunca las evitamos.

Es por eso que en este tipo de redes se utiliza un algoritmo llamado CSMA/CD, 

## Algoritmo CSMA/CD

este algoritmo hace lo siguiente:

* 1.- Cuando un equipo tiene un frame para enviar, escucha antes y no inicia el envio hasta que el medio ethernet no esta liberado.
* 2.- cuando el medio esta libre, el equipo empieza a enviar.
* 3.- Se puede dar el caso que 2 equipos empiezen a enviar a la vez cuando el medio esta libre, produciendo asi una colision
    * 3.1.- Los equipos la detectan y empiezan a enviar la señal que lo indica y de esta manera notifican que se producio una colision.
    * 3.2.- De manera independiente, los equipos que estaban enviando eligen un tiempo de espera al azar antes de volver a enviar.
    * 3.3.- Volvemos al punto 1 cuando se acaba el tiempo de esperar de uno de los equipos