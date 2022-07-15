# 4 Ejercicio Practico: Reto/Desafio Modos de Usuario.

Muchas veces lo que esta en un curso o en una pequeña documentacion x, no sera suficiente para realizar todas las cosas que necesitamos es por esto que muchas veces vamos a tener que investigar o buscar formas para realizar lo que necesitamos, es por esto que en este Ejercicio Practico es un Reto o Desafio porque se pide hacer cosas que no se han visto en el anterior Ejercicio practico y se tedra que buscar la solucion.

**El archivo inicial para este Ejercicio Practico es el "4 4 Modos de Usuario Inicial.pkt" que esta en la carpeta "Programas"**


## Cosas a realizar

las cosas que tenemos que realizar en este programa son:

* Acceder al Switch0 por consola desde el emulador de terminal del portatil y deshabilitar la interfaz de red que lo conecta al Switch1
    * Pista: Si colocas el cursor justo encima del punto verde que nos indica el estado de la interfaz, les mostrara el identificador de la interfaz asociada a este enlace.
    * Pista: Necesitaras ese indicador para acceder al submodo de configuracion correspondiente a ese interfaz.


El resultado esperado es el siguiente:

![Imagen13](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen13.png))

> **Note**: en caso de no saber utilizar el comando```?``` Todas las veces que sean necesarias

## Resolucion

Para realizar este desafio usaremos los siguientes comandos desde el emulador de terminal:

```
Cronos>enable
Cronos#configure terminal
Cronos(config)#interface FastEthernet 0/1
Cronos(config-if)#shutdown
```

> **Note**: Nos sirve para apagar/detener/deshabilitar la interfaz seleccionada de forma administrativa.

> **Note**: El resultado de esta practica se puede ver en el archivo "4 4 Modos de Usuario Final.pkt" que esta en la carpeta "Programas"