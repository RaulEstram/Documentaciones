# Introduccion a la configuracion de equipos Cisco CLI comman Line interface.

Para acceder a un equipo como lo es un Switch o un Router para configurarlo generalmente se hace mediante **CLI** (Command Line Interface o Interfaz de linea de comandos).

> **Note**: El CLI no es exclusivo de dispositivos de Red, tambien usamos este termino para las terminales de Windows o de Linux.

Un CLI es una herramiento que permite enviar instrucciones en modo TEXTO a un sistema operativo y visualizar los resultados. En pocas palabras es una interfaz que permite interactuar con el equipo.

## Gestionar un equipo: CLI vs Interfaz Grafica.

Para gestionar y configurar un equipo de Red tenemos tanto el CLI como las interfaces graficas que proporcionan algunos softwares, por ejemplo windows proporciona alguno para configurar las interfaces de red.

Teniendo esto en cuenta ¿Cuales son las diferencias?

* la Interfaz Grafica esta limitada en opciones de configuraciones, el CLI no pasa.
* Es mas intuitivo con la Interfaz Grafica.
* Mediante el CLI las acciones se realizan mucho mas rapido.
* Mediante el CLI podemos ir copiando y pegando instrucciones ya preparadas para realizar este proceso mucho mas rapido que con una Interfaz grafica cuando es necesario la velocidad.

Por lo tanto, el CLI siempre sera la opcion recomendada, y es mucho mas recomendada cuando sabemos que hay equipos que no tienen alguna interfaz grafica para gestionarlos.

## CLI - IOS

Cuando nos comunicamos con el CLI, en realidad lo estamos haciendo con el Sistema operativo que se esta ejecutando en ese equipo, en el caso de los Switches y Routers de Cisco el sistema operativo se llama **IOS** (Internetwork Operating System).

Hay que tener en cuenta esta parte, ya que por lo menos cada equipo de Cisco, puede llegar a tener varios IOS a travez del tiempo ya que se van actualizando constantemente porque se van descubriendo vulnerabilidades, errores, entre otros.

## Conectividad CLI-IOS

A nivel de conectividad, ¿Como nos conectamos o accedemos al CLI del IOS?

Podemos conectarnos al CLI de un Router o Switch mediante:
* SSH
* TELNET
* Consola

El metodo de acceso por consola nos sirve para configurar el equipo por primera vez, y para esto necesitamos conectar el equipo y nuestra computadora mediante un cable (El tipo de cable difiere entre equipo y equipo), por lo tanto requiere acceso fisico al equipo.

Los cables principales que se utilizan son:

* cable RJ-45 y adaptado DB-9 (Antes)
* Cable/conversor DB9/USB (Antes)
* Cable RJ-45 con DB9 + cable BD9 con USB (antes)
* RJ-45 a USB (actual)
* USB a Micro USB (Actual)

![Imagen 3](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen3.png)

Los metodos de acceso por SSH y Telnet se hacen utilizando la red TCP/IP, y esto tiene una gran ventaja ya que podemos estar lejos del equipo y aun asi gestionarlo, pero tiene la desventaja de que si la red se cea se pierde la gestion.

> **Note**: Para evitar que se pierda la coneccion a distancia cuando se cae la red que es cuando principalemente necesitamos gestionar los equipos aparece la Gestion OOB (Out Of Band o Fuera de Banda) que consta de tener una red paralela a la red de datos o de produccion, y en esta red solamente tenemos la gestion de los equipos. Por lo tanto cuando se cae la Red de Produccion podemos acceder a los equipos usando la Red de Gestion.


## Conectarnos al CLI

ya sabemos que para conectarnos fisicamente necesitamos un equipo como lo puede ser una laptop y diferentes cables dependiendo del equipo.

Una vez conectados fisicamente necesitamos un software especifico que nos permita la comunicacion y estos programas reciben el nombre de Emulador de Terminal.

> Un ejemplo de un programa que nos permite realizar la comunicacion es putty o PuTTY. Que es de codigo abierto y gratis.

Cuando queremos realizar la coneccion a equipos usando un Emulador de Terminal es necesario configurar el software, donde generalmente vamos a configurarlo con los siguientes parametros de consola:

* Puerto al que nos conectamos
* Velocidad: 9600 baud
* Data bits: 8
* Stop bits: 1
* Parity: No
* Flow control: No

