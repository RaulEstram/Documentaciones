# Dominios de colision

Podemos decir que todos los equipos que estan conectados a un HUB forman parte del mismo Dominio de colicion, Si tenemos 2 HUBs que estan conectados entre si,  este dominio de colision se extiende a los 2 HUBs y a todos los equipos conectados.

El dominio de colision hace referencia a todo el conjunto de quipos que tiene que aplicar el algoritmo CSMA/CD, por lo que, a media que crece la red el dominio de colision aumenta y por lo tanto hay mayor probabilidad de colision y menor rendimiento de la red.

## Bridge

El bridge es un dispositivo que surge por la problematica de crecer la red.

El Bridge Disminuye el tamaño de los dominios de colision, permite que 2 equipos (uno por dominio de colision) puedan enviar informacion a la vez. Esto lo hace de la siguiente manera:
* cuando le llega una trama, la pone en una cola de espera (utilizando memoria).
* luego comprueba si es necesario reenviarlo por el otro puerto o descartarlo.
* antes de reenviarlo: aplica el algoritmo CSMA/CD.

## Switch

Un Switch hace lo mismo que un Bridge pero en lugar de tener 2 puertos tiene muchos puertos, los switch tiene desde 8,16,24 a 48 puertos.

Gracias a esto disminuye el tamaño de los dominios de colision, y desde que se subtituyen todos los HUBs por Switches las redes estan libres de colisiones, por lo que ahora tenemos un sistema FULL Duplex en lugar de Half Duplex, esto permite que todos los diferentes dominios de colision puedan enviar de manera simultanea.

### Hay colisiones?

Como se dijo antes, desde que se sustituyen los Bridges por Switches ya no hay colisiones y esto se debe a que los cables que utilizan los switches tiene varios cables mas pequeños donde la mitad de estos se utilizan para enviar y la otra mitas para recibir informacion, por lo que podemos enviar y recibir informacion.

Esto no era posible con el Bringe, ya que envia informacion sin pensar, sin esperar y si 2 o mas equipos quieren enviar informaicon por un mismo cable o puerto, es donde se produce la colision.

El switch al contrario del Bridge, se espera y lo envia de forma ordenada por lo que evita las colisiones.

---

## ¿Por que sigue el termino de Dominio de colision?

A pesar de que los dominios de colisiones actualemente serial entre el equipo final y un switch (un dominio muy pequeño) todavia es posible llegar a tener alguna colision en algunos escenarios que normalmente son ocasionados por configuracion incorrecta en las interfaces y por problemas de Hardware.

por lo tanto nos quedaremos con lo siguiente:

**Por cada puerto de Switch es un dominio de colision y funcionara a FULL Duplex**.

## Ejemplo

Imaginemos que tenemos la siguiente red

![Imagen2]()

Con una capacidad de 100Mbps FULL Duplex tanto del Switch como de los PCs

### Cuantos dominios de Colision hay en la red?

Hay 9 dominios de colision.
Porque tenemos un switch y cada puerto del switch es un dominio de colision.


### Que ancho de banda tendra disponible cada PC?

Tendremos 100Mbps Full Duplex.
Porque los PCs se conectan a un Switch que ofrece el mismo ancho de banda full duplex.


### Pueden haber colisiones? 

Por norma general NO.

