# Funciones de los Routers: Routing y Forwarding

De forma general los Routers usan la informacion que tienen de la red contenida en la tabla de rutas para decidir por donde reenviaban el paquete.

> **Note**
> A la accion de decidir por donde enviar la informacion se llama **Routing** y a la accion de reenviar el paquete se le llama **Forwarding**.

Para que el Router realice el Forwarding necesita una tabla de Rutas.

## Tabla de Rutas de los Routers

A continuacion tenemos un ejemplo que una tabla de Rutas

| Direccion IP Destino | Mascara de Red | Next-Hop | Interfaz de Salida |
| :-: | :-: | :-: | :-: |
| 20.0.0.0 | 255.0.0.0 | 10.0.0.2 | Interface GI0/0 |
| 30.0.0.0 | 255.0.0.0 | Directamente Conectada | Interface GI0/1 |
| 10.0.0.0 | 255.255.255.0 | Directamente Conectada | Interface GI0/0 |


Los primeros dos campos nos dicen la **IP destino y su Netmask** cosas que ya se vieron con anterioridad.

Los ultimos 2 campos que son **Next-Hop e Interfaz de Salida** nos indica el siguiente salto y la interfaz de salida.

Esta tabla se interpretaria de la siguiente manera:

* Para llegar a la Direccion IP destino 20.0.0.0 con Netmask 255.0.0.0, habra que hacermo mediante el siguiente Router que es el 10.0.0.2 y llegaremos a el por la interfaz Gigabit 0/0.

* Para llegar a la Red 30.0.0.0 con Netmask 255.0.0.0 tendremos que ir por la interfaz GI0/1, y que la tiene directamente conectada.

## Ruta por defecto o Default Gateway

Una entrada habitual en la tabla de rutas es la Ruta por defecto o default gateway y podria aparecer en la tabla de Rutas de un modo similar al siguiente:

| Direccion IP Destino | Mascara de Red | Next-Hop | Interfaz de Salida |
| :-: | :-: | :-: | :-: |
| 0.0.0.0 | 0.0.0.0 | 10.0.0.2 | Interface GI0/0 |

Esta ruta es una ruta especial en donde cualquier IP hace MATCH en esta ruta.

Por lo tanto cuando un Router recive un paquete con un IP destino, el Router busca todas las posible rutas que puedan hacer match con el IP destino, esto quiere decir que siempre se realizara match con la ruta por defecto.

En estos casos es importante saber que el Router eligira la Ruta mas especifica para realizar el Forwarding, y la Ruta mas especifica sera la que tenga la Netmask con mas bits para la porcion de Red. 

> **Note** ya que la ruta por defecto siempre sera la menos especifica sabemos que solamente sera elegida cuando no se realice algun otro match con alguna ruta de la tabla de rutas.

## Rutas de Host

Tambien es posible que encontremos rutas que tengan como IP destino una direccion de Host, en otras palabras un equipo directamente, a estas rutas se les llaman Rutas de Host.

Estas rutas se caracterizan por tener la Netmask 255.255.255.255

## Tablas de Rutas de un Equipo

Las tablas de Rutas no son exclusivas de los Routers, Diferentes equipos tienen sus propias tablas de Rutas, nuestros equipos personales de computo tambien tienen sus propias tablas de rutas las cuales podemos visualizar.

### Visualizar la tabla de Rutas en Windows

para vizualizar las tablas de Rutas en Windows tenemos que realizar los siguientes pasos:

* Abrir la terminal
* digitamos el comando ```netstat -r```

Realmente solo nos va a interesar las primeras 2 rutas ya que todas las demas son rutas de Windows y no tiene gran importancia para nosotros.

Podemos ayudarnos a entender mejor la tabla de rutas usando el comando ```ipconfig /all``` para saber las IP de las interfaces de red y sus mascarad de red que estan en nuestros equipos.

### Visualizar la tabla de Rutas en Linux

Para visualizar las tablas de Rutas en Linux tenemos que realizar los siguientes pasos:

* Abrir terminal
* digitamos el comando ```netstat -r```


Podemos ayudarnos a entender mejor la tabla de rutas usando el comando ```ifconfig``` para visualizar los datos de red de nuestro equipo en linux.