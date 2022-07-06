# Visualizacion de procesos

Ejecutar un comando da como resultado algo llamado proceso. En el sistema operativo Linux, los procesos se ejecutan en función de los privilegios del usuario que ejecuta el comando. Esto permite que los procesos se limiten a ciertas funciones dependiendo de la identidad del usuario.

Aunque hay excepciones, generalmente el sistema operativo diferenciará entre los usuarios en función de si son o no el administrador. Normalmente, los usuarios habituales, no pueden controlar los procesos de otro usuario. Los usuarios que tienen privilegios administrativos, como la cuenta root, pueden controlar cualquier proceso de cualquier usuario, incluyendo la detención de cualquier proceso.


El comando **ps** se puede utilizar para enumerar los procesos.

```shell
$ ps [Opciones]
```
Por defecto, el comando **ps** mostrará los procesos que se están ejecutando en la terminal actual

La salida incluye las siguientes columnas de información:

- PID: El identificador para el proceso (process identifier), el cual es único para cada proceso. Esta información es útil cuando necesitamos controlar los procesos según su número identificador (ID).

- TTY: El nombre de la terminal en la que está funcionando el proceso. Esta información es útil para distinguir entre diferentes procesos que tienen el mismo nombre.

- TIME: La cantidad total de tiempo de procesado que utiliza un proceso determinado. Normalmente, los usuarios normales no utilizan esta información.

- CMD: El comando que inició el proceso.


En lugar de ver sólo los procesos que se están ejecutando en la terminal actual, los usuarios pueden querer ver todos los procesos que se están ejecutando en el sistema. La opción **-e** muestra todos estos proceso


```shell
$ ps -e
```

Muchas veces se puede utilizar la opción -f para proporcionar un resultado más detallado que incluya las opciones y los argumentos de cada proceso

```shell
$ ps -ef
```
