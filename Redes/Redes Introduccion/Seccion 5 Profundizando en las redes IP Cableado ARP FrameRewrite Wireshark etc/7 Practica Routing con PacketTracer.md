# Practica: Routing con PacketTracer.

Para esta practica tenemos las siguientes Redes interconectadas por un Router:

![Imagen36](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen36.png)

Lo que tiene esta practica es que ya tiene configuradas las IPs y MACs de los equipos finales, por otro lado los Switches practicamente no se les a movido nada.

Lo unico que vamos a configurar es el Router el cual por defecto tiene las interfaces DOWN o dehabilitadas y lo que tenemos que haces es habilitarlas y configurarlas.

## COnfiguracion de Router

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

> **Note** Podemos ver un pequeño resumen de la configuracion de las interfaces usando **```show ip interface brief```** o uno mas largo con **```show interfaces```**