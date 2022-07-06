# Sintaxis de comandos básicos

El terminal CLI es una poderosa herramienta y a menudo es el método principal utilizado para administrar dispositivos pequeños de bajo consumo, servidores de computación de gran capacidad en la nube, y mucho más. Una comprensión básica del terminal es esencial para diagnosticar y reparar la mayoría de los sistemas basados en Linux.


## ¿Qué es un comando?

Un comando es un programa de software que, cuando se ejecuta en la CLI (interfaz de línea de comandos), realiza una acción en el ordenador.

Cuando usted escribe un comando, el sistema operativo ejecuta un proceso para leer su entrada, manipular datos y producir resultados. Un comando ejecuta un proceso en el sistema operativo, que luego hace que el ordenador realice una tarea determinada.

## Sintaxis básica

La mayoría de los comandos siguen un patrón de sintaxis simple:

```linux
comando [opciones…] [argumentos…]
```

En otras palabras, escriba un comando, seguido de las opciones y/o argumentos antes de presionar la tecla Enter. Generalmente, las opciones (options) alteran el comportamiento del comando y los argumentos (arguments) son elementos o valores sobre los que debe actuar el comando. Aunque hay algunos comandos en Linux que no son completamente consistentes con estas normas de sintaxis, la mayoría de los comandos usan esta sintaxis o alguna similar.

---

### Argumentos

Un argumento (argument) se puede usar para especificar algo sobre lo que el comando debe actuar. 

Si al comando **ls** se le da el nombre de un directorio como argumento, obtendremos como resultado una lista del contenido de ese directorio.

ejemplo:
```linux
$ ls Documents
```
o
```linux
$ aptitude moo
```

---

### Opciones

Las opciones (options) se pueden utilizar para modificar el comportamiento de un comando.

El comando **ls** se utilizó para enumerar el contenido de un directorio, si le agregamos la opción **-l** vamos a obtener un resultado de “pantalla larga”, y proporcionar más información sobre cada uno de los archivos enumerado

```Linux
$ ls -l
```

A menudo, el carácter elegido para el comando es mnemotécnico de su propósito en inglés. Por ejemplo, la letra **l** para indicar largo (long) o **r** para invertir (reverse en inglés). De forma predeterminada, el comando ls imprime los resultados en orden alfabético, al agregar la opción **-r** se imprimirán los resultados en orden alfabético inverso.

```Linux
$ ls -r
```

Se pueden usar varias opciones a la vez, ya sea como opciones separadas como en **-l -r** o combinadas como **-lr**.

El resultado de los siguientes ejemplos sería el mismo:

```Linux
$ ls -l -r
$ ls -rl
$ ls -lr
$ ls -r -r
```

Los comandos pueden utilizar muchas combinaciones de opciones y argumentos. Las posibilidades para cada comando serán únicas.

