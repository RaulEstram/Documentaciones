# Cambiar el propietario de un archivo

Inicialmente, el propietario de un archivo es el usuario que lo crea. El comando **chown** se utiliza para cambiar el propietario de los archivos y directorios.

> Cambiar el usuario propietario requiere acceso administrativo. 

el comando chown permite cambiar el grupo propietario, lo cual *puede ser realizado por el usuario root o el propietario del archivo*.

Para cambiar el usuario propietario de un archivo, se puede utilizar la siguiente sintaxis. El primer argumento, [PROPIETARIO], especifica qué usuario debe ser el nuevo propietario. El segundo argumento, ARCHIVO, especifica el archivo al cual se está cambiando el propietario.

```terminal
$ chown [OPCIONES] [PROPIETARIO] ARCHIVO
```


