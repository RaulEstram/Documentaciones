# Administración de paquetes

La administración de paquetes es un sistema mediante el cual un software puede ser instalado, actualizado, consultado o eliminado de un sistema de archivos. En Linux, hay muchos sistemas de gestión de paquetes de software diferentes, pero los dos más populares son Debian y Red Hat. 

En el nivel más bajo del sistema de administración de paquetes Debian se encuentra el comando dpkg. Este comando puede ser complicado para los usuarios más nuevos a Linux. La herramienta Advanced Package Tool, apt-get, un programa front-end para la herramienta dpkg, facilita la gestión de paquetes.


> **Note**
> Un programa front-end es un programa que los usuarios pueden ver y con el que pueden interactuar.

> **Note**
> Muchos de los comandos de administración de paquetes requieren acceso administrativo, por lo que se precederán del comando sudo. 


## Instalacion de paquetes

Los paquetes de archivos normalmente se instalan por descarga directa desde repositorios ubicados en servidores de Internet. Los repositorios Debian contienen más de 65.000 paquetes de software diferentes. Antes de instalar un paquete, es recomendable actualizar la lista de paquetes disponibles usando el comando: 

```shell
$ apt-get update
```

Para buscar palabras clave (keyword) dentro de estos paquetes, puede utilizar el comando apt-cache search.

```shell
$ apt-cache search [keyword]
```

La palabra clave que se utiliza debe coincidir con parte del nombre o descripción del paquete que se intenta localizar. Se pueden usar varias palabras clave para especificar aún más la búsqueda; por ejemplo, el término de búsqueda web server proporcionará mejores resultados que web o server.

Un ejemplo es:

```shell
$ apt-cache search cow
```

Una vez encontrado el paquete (package) que desea instalar, puede utilizar el comando apt-get install para instalarlo:

```shell
$ sudo apt-get install {package}
```




## Actualizacion de paquetes

El comando **apt-get install** también puede actualizar un paquete, si ese paquete ya está instalado y existe una versión más reciente disponible. Si el paquete aún no está en el sistema, se instalará; si está en el sistema, se actualizará.

La actualización de todos los paquetes del sistema debe realizarse en dos pasos. Primero, actualice la caché de todos los paquetes disponibles utilizando **apt-get update**. En segundo lugar, ejecute el comando **apt-get upgrade** para actualizar todos los paquetes y sus dependencias.

```shell
$ apt-get update
$ apt-get upgrade
```

## Eliminacion de paquetes

El comando apt-get puede eliminar o purgar un paquete. La diferencia entre los dos es que purgar suprime todos los archivos del paquete, mientras que eliminar suprime todos los archivos del paquete, excepto los archivos de configuración.

Un administrador puede ejecutar el comando **apt-get remove** para eliminar un paquete o el comando **apt-get purge** para purgar un paquete completamente del sistema.

**Eliminar o remove**

```shell
$ apt-get remove {package}
```


**Purgar o purge**

```shell
$ apt-get purge {package}
```


