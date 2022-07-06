# Apagar

El comando **shutdown** prepara el sistema para un apagado seguro. Todos los usuarios que han iniciado una sesión reciben la notificación de que el sistema se está apagando y se evitan nuevos inicios de sesión en los cinco minutos previos al apagado completo del sistema.

```shell
$ shutdown [OPCIONES] HORA [MENSAJE]
```

> **Note**
> El comando shutdown requiere acceso administrativo

Ejemplo:

```shell
$ shutdown now
```

A diferencia de otros comandos utilizados para apagar el sistema, el comando **shutdown** requiere un argumento de tiempo para especificar cuándo debe comenzar el apagado. Los formatos de este argumento de tiempo pueden ser la palabra now (ahora), una hora del día en el formato hh:mm o el número de minutos de retraso utilizando el formato +minutos.

> **Warning**
> El reloj de nuestro sistema puede estar configurado en una zona horaria diferente a la que se encuentra usted. Para verificar la hora en la terminal, use el comando date.


El comando shutdown también posee la opción de añadir un mensaje como argumento. Este mensaje aparecerá en las terminales de todos los usuarios.

```shell
$ shutdown now 'hasta la vista baby'
```



