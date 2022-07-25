# Frame Rewrite

El **Frame Rewrite** es una parte Sumamente **importante** y clave para entener las **comunicaciones IP.**

El **Frame Rewrite** se refiere al **encapsulado de los datos al atravesar las redes**. El router que esta en nivel 3, **desencapsula y reescribe los frames de nivel 2 para poder alcanzar su destino**.

El Frame Rewrite se entiende de mejor manera al utilizar un ejemplo:

![Imagen41](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen41.png)

En esta imagen podemos ver como las direcciones MAC cambian al querer realizar una comunicacion entre el equipo con la ip 30.0.0.50 y el equipo con la ip 40.0.0.10.

Este proceso donde cambian las direcciones MAC que se encuentran en la Trama o Frame se le conoce como Frame Rewrite y esto se debe a que al querer realizar esta comunicacion no se conoce la MAC destino porque no esta en la misma red, por lo tanto al Realizar el envio la primera direccion MAC Destino es la MAC de la Interfaz del Router de la Red.

Una vez que el paquete llega al Router de Desencapsula y se reescribe las direcciones MAC del Frame, donde el nuevo MAC Origen es la Interfaz por donde va a salir el nuevo Frame y el MAC Destino sera el MAC de equipo final con el ip 40.0.0.10.

> **Note** Recordemos que Cada Router posee una tabla ARP que podemos visualizar con el comando ```show arp``` desde el modo privilegiado, Esta tabla tiene las IPs asociadas a cada MAC.


Gracias al Frame Rewrite se dice que la **capa 2 es Hop-to-Hop Delivery** porque se encarga de la entrega en forma de saltos y que la **capa 3 es End-to-End Delivery** porque se encarga de la entrega de extremo a extremo de la comunicacion

Por ultimo a continuacion podemos visualizar un ejemplo mas complejo del Frame Rewrite donde se utilizan mas Routers:

![Imagen42](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen42.png)