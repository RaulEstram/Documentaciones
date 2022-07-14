# Ejercicio Practico: Modos de Usuario de la CLI.

Con este ejercicio practico se tiene planeado se se vean las siguientes cosas:

* Conectarnos por consola y emulador de terminal a un equipo.
* Pasar de un modo de usuario a otro.
* Cambiar el Hostname de un equipo.
* Ver los diferentes comandos que nos permite cada modo.

## Pasos

### 1.- crearemos el siguiente ecenario

![Imagen5](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen5.png)

Usamos cable de cobre cruzado para interconectar equipos de la misma capa.

### 2.- conectamos por consola al portatil al switch0.

![Imagen6](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen6.png)

conectamos con cable de consola desde el puerto de consola del switch al RS232.

### 3.- Acceder con el emulador de terminal del portatil a la consola del switch0.

![Imagen7](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen7.png)

Desde el portatil, vamos al terminal en desktop y entramos al terminal.

> **Note**
> En que modo estamos?
> En modo terminal

### 4.- Escribir "?"

Al escribir este signo de interrogacion, podremos ver los posibles comandos que nos permite ejecutar la termimanl en el modo en el que estamos.

![Imagen8](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen8.png)

cuando escribimos algun comando que necesita mas parametros podemos escribir nuevamente el signo ```?``` para ver las cosas que podemos agregar.

En caso de que solamente se muestre un ```<cr>``` significa que ya no podemos agregar mas y que espera un enter.

![Imagen9](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen9.png)

### 5.- Pasar al modo EXEC Privilegiado.

para entrar en este modo es necesario usar el comando ```enable```.

Desde este modo podemos usar ```?``` para ver todos los comandos que podemos usar en este modo.

![Imagen10](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen10.png)

### 6.- Ir al modo de configuracion y mirar las opciones de este modo para la opcion de cambiar el nombre del equipo.

Para esta parte tenemos que combiar el nombre del equipo desde el modo de configuracion global.

![Imagen11](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen11.png)

Podemos ver como cambia el nombre del equipo en el prompt

### 7.- Hacer lo mismo para el segundo Switch

![Imagen12](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen12.png)