# Acceso administrativo

Hay muchos comandos de Linux que tratan con información confidencial como contraseñas, hardware del sistema, u otros que operan bajo circunstancias excepcionales. Evitar que usuarios ordinarios ejecuten estos comandos ayuda a proteger el sistema. Iniciar una sesión como usuario root proporciona acceso administrativo, y permite la ejecución de algunos de los comandos privilegiados.

## El comando **SU**

```terminal
$ su [Opciones] NOMBRE-DE-USUARIO
```

El comando **su** le permite actuar temporalmente como un usuario diferente. Lo hace creando un nuevo shell. El shell es simplemente una consola de entrada de texto que le permite escribir comandos.

**De forma predeterminada, si no se especifica una cuenta de usuario**, el comando **su** abrirá un nuevo shell **como usuario root**, proporcionando privilegios administrativos.

Y para salir de este modo usaremos el comando **exit**.

## El comando **sudo**

```terminal
$ sudo [Opciones] COMANDO
```

El comando sudo permite a un usuario ejecutar un comando como otro usuario sin tener que crear un nuevo shell. 

Para ejecutar un comando con privilegios administrativos utilice el comando como argumento para el comando sudo. 

Al igual que pasa con el comando su, el comando sudo asume por defecto que la cuenta de usuario root debe usarse para ejecutar comandos.

> :warning: El comando sudo también puede usarse para cambiar a otras cuentas de usuario. Para especificar una cuenta de usuario diferente, utilice la opción -u.


 El comando sudo sólo proporciona acceso administrativo para la ejecución del comando especificado. Esto es una ventaja ya que reduce el riesgo de que un usuario ejecute accidentalmente un comando como usuario root.


