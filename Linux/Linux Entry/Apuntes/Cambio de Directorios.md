# Cambio de Directorios

Los archivos se utilizan para almacenar datos como texto, gráficos y programas. Los directorios son un tipo de archivo utilizado para almacenar otros archivos: proporcionan una estructura organizativa jerárquica.

Para poder movernos entre directorios utilizamos el comando **cd**

```Linux
$ cd [opciones] [ruta]
```

Los directorios son equivalentes a las carpetas en Windows y Mac OS. Al igual que estos sistemas operativos más populares, una estructura de directorios Linux también tiene un nivel superior. No se llama “Mi PC”, sino directorio raíz (root) y está representado por el carácter **/**. Para desplazarse al directorio root, utilice el carácter / como argumento del comando cd.

```Linux
$ cd /
```

El argumento para el comando **cd** es más que el nombre de un directorio, en realidad es una ruta (path). Una ruta es una lista de directorios separados por el carácter /. Por ejemplo, /home/{user} que seria la ruta a su directorio de inicio


## Rutas absolutas

Una ruta absoluta le permite especificar la ubicación exacta de un directorio. Siempre comienza en el directorio root, por lo tanto siempre comienza con el carácter **/**. un ejemplo es:

**/home/user/Documents**


## Rutas relativas

Una ruta relativa ubica un archivo en relación con la ubicación actual del usuario en el sistema de archivos. Las rutas relativas no comienzan con el carácter /, comienzan con el nombre de un directorio. Un ejemplo es:

Documents/Directory1/Directory2

## Accesos Directos o Atajos 

### Dos puntos ..

Independientemente del directorio en el que se encuentre, el carácter .. siempre representa un directorio superior en relación al directorio actual, a veces denominado directorio padre. 

---

### Un punto .

Independientemente del directorio en el que se encuentre, el carácter . siempre representa su directorio actual. 

---

### El símbolo ~

El directorio principal del usuario actual está representado por el carácter **~** .









