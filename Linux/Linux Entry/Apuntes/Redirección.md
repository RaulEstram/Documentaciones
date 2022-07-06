# Redirección

Agregar contenido a archivos en Linux puede hacerse de varias maneras. Linux posee algunos editores de texto que pueden usarse para agregar contenido a un archivo. Sin embargo, este método requiere cierta familiaridad con los comandos del editor de texto de Linux.

En Linux, se puede agregar contenido a un archivo rápidamente usando una función de línea de comandos llamada redirección de entrada/salida (E/S) (input/output; I/O). La redirección E/S (I/O) permite enviar la información de la línea de comandos a archivos, dispositivos y otros comandos. 


Cuando se trata de comandos de entrada y salida, existen tres rutas, o “vías”. Estas rutas se denominan descriptores de archivos. 

- El primer descriptor de archivo es la entrada estándar, abreviada como **STDIN (standard input)**. La entrada estándar es la información que el comando recibe y procesa cuando se ejecuta, esencialmente lo que un usuario escribe en el teclado. 

- El segundo descriptor de archivo es la salida estándar, abreviada como **STDOUT (standard output)**. La salida estándar es la información que muestra el comando, la salida del comando. 

- El último descriptor de archivo es el error estándar, abreviado como **STDERR (standard error)**. **STDERR**, son los mensajes de error generados por comandos que no se ejecutan correctamente. 


Los siguientes son ejemplos de cómo aparecerán los descriptores de archivos en la terminal:


### Entrada estándar (STDIN)

```shell
$ sysadmin@localhost:~$ ls ~/Documents
```

### Salida estándar (STDOUT)

```shell
$ sysadmin@localhost:~$ ls

Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
```

### Error estándar (STDERR)

```shell
$ sysadmin@localhost:~$ ls fakefile                                           
ls: cannot access fakefile: No such file or directory
```


Esta sección cubrirá uno de los tres descriptores de archivos, **STDOUT**, y cómo redirigir **STDOUT** desde donde normalmente aparece en el terminal, a un archivo en el sistema de archivos. Para ejecutar la redirección, simplemente use el símbolo “mayor que” **>** junto al nombre del archivo:

```shell
$ {COMANDO} > {ARCHIVO}
```

Para demostrar cómo funciona la redirección, usaremos la salida del comando cat. 


```shell
$ cat texto.txt > textoRediregido.txt
```

Si queremos agregar mas informacion a un archivo usando la redireccion necesitaremos utilizar **>>** en lugar de **>** ya que este primero agrega la informacion y el segundo reescribiria todo el contenido.

```shell
$ echo "agregando este texto" >> textoRediregido.txt
```

> **Warning**
> Para redirigir la información a un archivo existente, el usuario debe tener permisos de escritura para ese archivo.



