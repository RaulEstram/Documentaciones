# Introduciendo las variables del BASH shell

**Una variable del shell BASH es una función que te permite a ti o al shell almacenar los datos**. Esta información puede utilizarse para proporcionar información crítica del sistema o para cambiar el comportamiento del funcionamiento del shell BASH (u otros comandos).

Las **variables reciben nombres y se almacenan temporalmente en la memoria. Al cerrar una ventana de la terminal o shell, todas las variables se pierden.** Sin embargo, el sistema automáticamente recrea muchas de estas variables cuando se abre un nuevo shell.

### Ejemplo impresion y modificacion de una variable

La variable HISTSIZE define cuántos comandos anteriores se pueden almacenar en la lista del historial. Para mostrar el valor de la variable debes utilizar un carácter del signo de dólar \$ antes del nombre de la variable. Para modificar el valor de la variable, no se utiliza el carácter $:

```shell
sysadmin@localhost:~$ HISTSIZE=500
sysadmin@localhost:~$ echo $HISTSIZE 500                                                             
sysadmin@localhost:~$
```

## La Variable PATH

Una de las variables del shell BASH más importante que hay que entender es la variable PATH.

El término path se refiere a una lista que define en qué directorios el shell buscará los comandos. Si introduces un comando y recibes el error "command not found", es porque el shell BASH no pudo localizar un comando por ese nombre en cualquiera de los directorios en la ruta.

Si en tu sistema tienes instalado un software personalizado, puede que necesites modificar la ruta PATH para que sea más fácil ejecutar estos comandos. 

## Comando export

Hay dos tipos de variables utilizadas en el shell BASH, la local y la de entorno. Las variables de entorno, como PATH y HOME, las utiliza el BASH al interpretar los comandos y realizar las tareas. Las variables locales son a menudo asociadas con las tareas del usuario y son minúsculas por convención. Para crear una variable local, simplemente introduce:

```shell
sysadmin@localhost:~$ variable1='Something'
```

Para ver el contenido de la variable, te puedes referir a ella iniciando con el signo de $:

```shell
sysadmin@localhost:~$ echo $variable1
Something
```

**Después de exportar** variable1 con el **comando export** llegará a ser **una variable de entorno**. 


```shell
sysadmin@localhost:~$ export variable1 
sysadmin@localhost:~$ env | grep variable1
variable1=Something
```


> **Note** Para ver las variables de entorno, utiliza el comando **env**. El comando **grep** es una herramienta que se utiliza para buscar patrones de texto en un archivo o en la salida de otro comando. Cuando se utiliza con el operador "|" (pipe), se le llama "pipelining" y permite encadenar dos o más comandos en Unix-like systems, enviando la salida del primer comando como la entrada del segundo.

**Las variables exportadas pueden eliminarse con el comando unset**



> **NOTE** Las variables creados de esta manera sólo persistirán mientras el shell esté abierto. Una vez que el shell es cerrado, las nuevas variables que hayas creado, se perderán.