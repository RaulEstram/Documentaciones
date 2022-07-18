# Ejercicio Practico: Switching

Para ver de mejor forma el uso de los cables cruzados y rectos realizaremos lo siguiente en PacketTracer.

![Imagen21](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen21.png)

## crear las conecciones

Lo primero que tenemos que hacer es posicionar y conectar todos los equipos.

Si lo hicimos bien nos quedara algo similar a lo siguiente:

![Imagen22](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen22.png)

## Cambiar las MAC

Para cambiar las direcciones MAC de un equipo en PacketTracer tenemos que ir a "Config" y a FastEhernet 0 por ejemplo de "Interace".

Y en la parte que dice "MAC Address" podremos cambiar la direccion MAC.

![Imagen23](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen23.png)

## Cambiar nombres a unos mas intuitivos.

Cambiaremos los nombres de los equipos para que tengan unos nombres mas intuitivos a la vista.

![Imagen24](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen24.png)

## Cambiar los Hostname de los Switches

Vamos a tener que ponerles los nombres de:

* SW_Oficina
* SW_Taller

Entonces nos quedan de la siguiente manera:

* SW_Oficina

![Imagen25](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen25.png)

* SW_Taller

![Imagen26](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen26.png)

## Configurar IPs

Para configurar las IPs tenemos que ir a Config>Interface>FastEthernet>IP Address y ahi pondremos la IP de nuestros equipo

![Imagen27](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen27.png)


## Ver las tablas de direcciones MAC de los Switches.

Para visualizar las tablas de direcciones MAC de algun Switch tenemos que estar en su CLI en modo privilegiado y usar el comando ```show mac-address-table``` o el comando ```show mac address-table```

![Imagen28](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen28.png)


## Probar conectividad

Para probar la conectividad de esta Red tanto a Capa 1, 2 y 3 hay un comando llamado **ping**

Para realizar esta comprobacion los equipos finales tienen que tener una IP, que es lo que hicimos en un punto anterior.

Para realizar un **ping** tenemos que cambiar de modo **realtime** al modo **simulation** que se encuentra en la parte inferior derecha. 

Una vez que cambiamos el modo usaremos el siguiente comando desde algun equipo final como un portatil:

```bash
C:\>ping {ip Destion}
```

Gracias al modo de simulacion y de ping podremos ver como va viajando el ping a traves de nuestra Red.

## Limpiar tabla de direcciones MAC

Para limpiar las tablas de direcciones MAC de nuestros Switch tenemos que digitar el comando ```clear mac-address-table``` desde el modo privilegiado.

---

> **Note** El programa finalizado esta en la carpeta Programas con el nombre "5 2 Switching.pkt". 