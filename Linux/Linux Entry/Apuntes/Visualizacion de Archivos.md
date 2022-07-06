# Visualizacion de Archivos

Existen varios comandos en Linux disponibles para visualizar el contenido de los archivos. El comando **cat**, que significa “concatenar”, a menudo se usa para ver rápidamente el contenido de archivos pequeños.

El comando **cat** mostrará todo el contenido del archivo

> se recomienda principalmente para archivos pequeños para los que el resultado es limitado y no requiere desplazamientos de pantalla.

Para ver el contenido de un archivo utilizando el comando cat, simplemente escriba el comando y utilice el nombre del archivo que desea ver como argumento:

```terminal
$ cat [OPCIONES] [ARCHIVO]
```


Otra forma de ver el contenido de los archivos es utilizando los comandos **head** y **tail**. Estos comandos se utilizan para ver un número seleccionado de líneas desde la parte superior o inferior de un archivo.

**head**
```terminal
$ head [OPCIONES] [ARCHIVO]
```
**tail**
```terminal
$ tail [OPCIONES] [ARCHIVO]
```


La opción **-n** con los comandos **head** y **tail** se puede utilizar para especificar la cantidad de líneas a mostrar.

```terminal
$ {head | tail} -n número_de_líneas archivo
```





