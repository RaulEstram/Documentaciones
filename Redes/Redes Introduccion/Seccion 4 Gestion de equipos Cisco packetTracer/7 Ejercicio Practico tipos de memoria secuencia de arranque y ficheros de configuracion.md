# Ejercicio Practico: tipos de memoria, secuencia de arranque y ficheros de configuracion.

El objetivo de esta practica es:
* Diferenciar el startup-config y el running-config
* Reescribir la startup-config.
* reiniciar un equipo
* ver contenido de la memoria Flash y la version de la IOS.

Para esta practica tamos a tener el siguiente escenario.

![Imagen14](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen14.png)

> **Note** Podemos encontar este escenario en el archivo "4 7 Memorias_Configuraciones.pkt" de la carpeta "Programas"


## Ver configuracion de los Routers

Para ver la configuracion de los equipos tendremos que usar su CLI para ingresar los siguientes comandos:

```cli
Tijuana>enable
Tijuana#show running-config
```
![Imagen15](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen15.png)

Con los anteriores 2 comandos podremos ver toda la configuracion activa del equipo.

Para ver la configuracion de inicio ahora utilizaremos el comando ```show startup-config```

![Imagen16](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen16.png)

## Reescribir la configuracion de inicio por la configuracion activa

Para Guardar la configuracion que se hizo en la configuracion activa en la configuracion de inicio tendremos que usar el comando ```copy running-config startup-config ```  o el comando ```write```.

Para esto primero realizaremos un cambio en la configuracion de algun Router, este cambio sera que apagaremos o deshabilitemos la interfaz con la que se conecta al otro Router, Los comandos que utilizaremos seran: 

```cli
Tijuana>enable
Tijuana#configure terminal
Tijuana(config)#interface gigabitEthernet 0/0
Tijuana(config-if)#shutdown
```

Posteriormente regresaremos al modo Privilegiado.

```cli
Tijuana(config-if)#exit
Tijuana(config)#exit
Tijuana#

```

Por ultimo reescribiremos la configuracion de incio usando el siguiente comando:

```cli
Tijuana#copy running-config startup-config 
```

Con esto habremos realizado todos los cambios adecuadamente y los habremos guardado.

![Imagen17](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen17.png)



## reiniciar un Equipo

Para reiniciar un Equipo utilizaremos el siguiente comando desde el modo Privilegiado: ```reload```

![Imagen18](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen18.png)


## Ver contenido de la memoria Flash y version del IOS

Para ver el contenido de la memoria flash usaremos el comando ```show flash```

![Imagen19](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen19.png))

Para ver la version del IOS usaremos el comando ```show version```

![Imagen20](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen20.png))