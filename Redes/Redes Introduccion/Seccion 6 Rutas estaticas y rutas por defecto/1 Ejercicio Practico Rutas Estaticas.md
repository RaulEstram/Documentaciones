# Ejercicio Practico: Rutas Estaticas.

Para este ejercicio vamos a tener el siguiente ejemplo:

![Imagen43](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen43.png)

Para aprender que son las Rutas Estaticas tenemos que empezar a realizar algunas cosas que ya hemos visto.

## Configurar las interfaces de los Routers

Para configurar la interfaz del RouterOficina usaremos los comandos:

```terminal
RouterOficina>enable 
RouterOficina#configure terminal 
RouterOficina(config)#interface gigabitEthernet 0/1
RouterOficina(config-if)#ip address 10.100.100.1 255.255.255.0
RouterOficina(config-if)#no shutdown 
```

Para configurar la interfaz del RouterTaller usaremos los comandos:

```terminal
RouterTaller>enable 
RouterTaller#configure terminal 
RouterTaller(config)#interface gigabitEthernet 0/1
RouterTaller(config-if)#ip address 10.100.100.2 255.255.255.0
RouterTaller(config-if)#no shutdown 
```

Una vez hecho esto podemos ver como las interfaces ya estan habilitadas y tambien que ya estan configuradas si usamos el comando ```show ip interfaces brief```, a su vez podemos ver las tablas de Rutas de los Routers con el comando ```show ip route```.

Si miramos las tablas de Rutas, veremos que tanto el RouterOficiana como el RouterTaller no saben como llegar a la Red del otro y es por eso que todabia no hay comunicacion, y es en este momento en donde entran las **Rutas Estaticas y las Rutas Dinamicas**

* **Rutas Estaticas**: Son aquellas rutas que ingresa el administrador en un equipo de Red de forma manual.
* **Rutas Dinamicas**: Son aquellas que no configura manualmente el administrador, se crean automaticamente gracias a un Protocolo de Enrutamiento que tenemos que configurar en los Routers que queremos que participen en esa comunicacion.

## Configurar Rutas Estaticas.

La sintaxis que nos permite agregar una Ruta Estatica en un Router desde el modo de configuracion global es la siguiente:

```terminal
Router(config)#ip route {direccion ip destino} {mascara de red del ip destino} {ip del siguiente salto}

La forma para configurar una Ruta Estatica en nuestro ejemplo con el RouterOficina seria el siguiente codigo:

```terminal
RouterOficina>enable 
RouterOficina#configure terminal 
RouterOficina(config)#ip route 10.2.2.0 255.255.255.0 10.100.100.2
```

Posteriormente si revisamos la tabla de Rutas de neustro RouterOficina veremos lo siguiente:

```terminal
RouterOficina#show ip route 
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

     10.0.0.0/8 is variably subnetted, 5 subnets, 2 masks
C       10.1.1.0/24 is directly connected, GigabitEthernet0/0
L       10.1.1.1/32 is directly connected, GigabitEthernet0/0
S       10.2.2.0/24 [1/0] via 10.100.100.2
C       10.100.100.0/24 is directly connected, GigabitEthernet0/1
L       10.100.100.1/32 is directly connected, GigabitEthernet0/1

RouterOficina#
```

Lo que podemos ver es que se agrega un Ruta de tipo estatica o static que nos dice que para llegar a la red 10.2.2.0/24 lo hara via 10.100.100.2.

Ahora si queremos agregar una Ruta Estatica en el Router Taller para que se pueda comunicar con la red 10.1.1.0/24 usaremos los siguientes comandos:

```terminal
RouterTaller>enable 
RouterTaller#configure terminal 
RouterTaller(config)#ip route 10.1.1.0 255.255.255.0 10.100.100.1
```

Tambien podemos comprobar su tabla de rutas para comprobar que se realizo de la forma adecuada.

## Configurar los default gateways

SI probamos la conectividad entre las redes nos daremos cuenta que no sera posible por la comunicacion ya que todavia no estan configurados los default gateways de los equipos finales, y como anteriormente los vimos, es muy facil, simplemente apregamos el ip de la interfaz del Router en los equipos finales como su default gateway.


> **Warning** En caso de que no aparescan las Rutas estaticas en la tabla de rutas podemos ver si se agregaron usando el comando ```show running-config``` en la seccion de **ip classless**