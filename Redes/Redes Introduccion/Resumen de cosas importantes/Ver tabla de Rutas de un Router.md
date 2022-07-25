# ver tabla de Rutas de un Router

La tabla de Rutas nos sirve para ver a donde se redirigen cada interfaz de un Router, y para poder visualizar esta tabla tenemos que tener previamente configuradas las interfaces del Router donde deben de tener a que IP de dirigen cada Interfaz.

Para esto tenemos que usar el comando ```show ip route``` desde el modo privilegiado del CLI del Router.

El comando que utilzaremos y su respuesta es similar a lo siguiente:

```
Router#show ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

     10.0.0.0/8 is variably subnetted, 4 subnets, 2 masks
C       10.1.1.0/24 is directly connected, GigabitEthernet0/0
L       10.1.1.1/32 is directly connected, GigabitEthernet0/0
C       10.2.2.0/24 is directly connected, GigabitEthernet0/1
L       10.2.2.1/32 is directly connected, GigabitEthernet0/1
```