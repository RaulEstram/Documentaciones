# Ejercicio Practico: Rutas por defecto.

Habiamos visto que las rutas por defecto son rutas en la cual hacen match todas las direcciones IPs, esta ruta por defecto se representaba con la ip 0.0.0.0/0.

Esta ruta hace la funcion de comodin por asi decirlo y solamente sera utilizada cuando no se realize un match con ninguna otra ruta.

La Ruta por Defecto no es nada mas y nada menos que una Ruta por defecto y para esto usaremos el siguiente esenario:

![Imagen46](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen46.png)

> **Note** Este Escenario lo encontraremos en la carpeta "Programas" con el nombre "6 2 PracticaRouting Inicio.pkt"

> **Note** Este ejercicio se encuentra finalizado en la carpeta "Programas" con el nombre "6 2 PracticaRouting Final.pkt"

## Configurar Interfaces

Ya hemos visto como realizar esto varias veces asi que no se planea profundizar en esto, simplemente que la forma como se debe de ver nuestras redes debe de ser de la siguiente manera:

![Imagen47](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen47.png)

## Configurar Rutas Estaticas

En este punto tenemos que configurar las rutas Estaticas en el RouterCentral para saber como se van a conectar con las 3 redes.

Esta configuracion se realizaria con los siguientes comandos:

```termianl
Router>enable 
Router#configure terminal 
Router(config)#ip route 10.2.2.0 255.255.255.0 10.200.200.2
Router(config)#ip route 10.3.3.0 255.255.255.0 10.50.50.2
Router(config)#ip route 10.1.1.0 255.255.255.0 10.100.100.2 
```

Podemos asegurarnos de que se agregaron adecuadamente, lo cual nos daria la siguiente respuesta:

```terminal
Router#show ip route static 
     10.0.0.0/8 is variably subnetted, 9 subnets, 2 masks
S       10.1.1.0/24 [1/0] via 10.100.100.2
S       10.2.2.0/24 [1/0] via 10.200.200.2
S       10.3.3.0/24 [1/0] via 10.50.50.2

Router#
```

## Configurar Rutas por defecto 

Al principio vimos que las rutas por defecto son rutas en donde siempre se hace match y que practicamente son Rutas Estaticas, es por esto que vamos a configurar o agregar estas rutas a todos los Routers que no sean el Router Central para ahorrarnos lineas de comando.

Si no usaramos Rutas por defecto tendriamos que agregar 2 rutas en cada Router que conecta a una Red, por lo que quedaria algo similar a lo siguiente:

![Imagen48](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen48.png)

Para evitar agregar rutas de "mas" podemos usar rutas por defecto por lo que solamente se utilizaran los siguientes comandos:

* Router Oficina


```terminal
RouterOficina>enable 
RouterOficina#configure terminal 
RouterOficina(config)#ip route 0.0.0.0 0.0.0.0 10.100.100.1
``` 

* Router Almacen

```terminal
RouterAlmacen>enable 
RouterAlmacen#configure terminal 
RouterAlmacen(config)#ip route 0.0.0.0 0.0.0.0 10.50.50.1
```

* RouterTaller

```terminal
RouterTaller>enable 
RouterTaller#configure terminal 
RouterTaller(config)#ip route 0.0.0.0 0.0.0.0 10.200.200.1
```

Una vez hecho lo anterior ya tendremos configurado todo nuestro esenario y ya se podran realizar pings desde cualquier computadora de un red a otra de otra red.
