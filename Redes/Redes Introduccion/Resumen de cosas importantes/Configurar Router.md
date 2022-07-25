# Configurar un Router

Para configurar un Router es necesario levantar sus interfaces y posteriormente configurar sus interfaces.

## Levantar o habilitar Interfaces de un Router

Para habilitar las interfaces de un Router tenemos que ir a la configuracion global del Router y de ahi entrar al Submodo de configuracion de cada interfaz y utilizar el comando ```no shutdown```.


## Configurar Interfaces de un Router

una vez que habilitamos la interfaz de un Router podemos configurarlo, esto implica que debemos agregar a que Red va o se dirige esa interfaz, para esto utilizaremos el comando ```ip address {ip} {subnet mask}``` desde el submodo de configuracion de cada interfaz.

Ejemplo de comandos que utilizaremos:

```bash
Router>enable
Router#configure terminal 
Router(config)#interface gigabitEthernet 0/1
Router(config-if)#ip address 10.2.2.1 255.255.255.0
```

Respecto al IP que utilizaremos en el comando, en realidad no hay ninguna norma que obligue a asignar una dirección u otra para la interfaz del router, el único requisito es que sea una dirección IP de Host válida, es decir, que no sea ni Dirección IP de Red ni de Broadcast.

Lo que se suele hacer en la práctica es reservar un rango de IPs para equipos de red dentro de cada Red IP.

Por ejemplo, si una empresa tiene 2 redes internas, la 192.168.1.0/24 y la 192.168.2.0/24, se podrían reservar las 10 primeras de cada red para asignar a los posibles equipos de red que se acaben conectando a esa red:

- 192.168.1.1- 192.168.1.10: Reservadas

- 192.168.2.1- 192.168.2.10: Reservadas

Y al router le podríamos asignar la que acaba en .1 para cada una de las redes.

También es muy habitual reservar las últimas en lugar de las primeras. En este caso los routers tendrían direcciones del tipo: 192.168.1.254 o 192.168.2.254.

Esto se suele hacer así para que sea más fácil para los administradores de la red el saber (de memoria) qué dirección toma el router (gateway) de la red.

Pero a nivel funcional, recuerda que cualquier direccion IP de Host es valida
