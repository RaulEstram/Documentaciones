# Listado de archivos

El comando **ls** se utiliza para enumerar el contenido de un directorio. 

```linux
$ ls [Opciones] [Archivo]
```

De forma predeterminada, el comando ls usado sin opciones o argumentos mostrará los archivos contenidos en el directorio actual

## ls -l

Para obtener información detallada sobre los archivos, como el tipo de archivo, los permisos, las propiedades o el sello horario, ejecute una lista larga utilizando la opción **-l** con el comando ls.

Cada línea corresponde a un archivo contenido en el directorio. La información sobre cada archivo se puede dividir en campos separados por espacios. Los campos son los siguientes

```terminal
-rw-r--r-- 1 root   root  18047 Dec 20  2017 alternatives.log       
            
drwxr-x--- 2 root   adm    4096 Dec 20  2017 apache2  
```
---

### Tipo de archivo
El primer campo contiene en realidad diez caracteres. El primer carácter indica el tipo de archivo y los nueve siguientes especifican permisos. Los tipos de archivo son:


| Símbolo  |  Tipo de Archivo |  Descripcion |
|-|-|-|
|d|	directorio	|Un archivo usado para contener otros archivos.|
| - |	archivo ordinario|	Incluye archivos leíbles, imágenes, archivos binarios, y archivos comprimidos.|
|l	|enlaces simbólicos|	Apunta a otro archivo.|
|s	|socket|	Permite la comunicación entre procesos.|
|p	|tubería (pipe)|	Permite la comunicación entre procesos.|
|b	|archivo bloque|	Usado para comunicaciones con el equipo (hardware).|
|c	|archivo carácter	|Usado para comunicaciones con el equipo (hardware).|
---
### Permisos

Los permisos indican cómo determinados usuarios pueden acceder a un archivo.
Y los permisos son los siguientes 9 caracteres del primer campo

---

### Numero de enlaces directos

Es el segundo campo y este número indica cuántos enlaces directos apuntan a este archivo.
(Enlaces directos esta fuera de este turorial pero esta en el tutorial de Linux Essentials)

---

### Propietario del archivo

Es el tercer campo y nos dice a quien le pertenece ese archivo.

Cada vez que se crea un archivo, la propiedad se asigna automáticamente al usuario que lo creó.

---

### Grupo propietario del archivo

Es el cuerto campo e indica que grupo posee este archivo.

---

### Tamaño del archivo

Es el quinto campo e indica el tamaño de los archivos en bytes.

Los directorios y archivos más grandes pueden mostrarse en kilobytes ya que mostrar su tamaño en bytes resultaría en un número demasiado grande. 

---

### Sello horario o de tiempo

Es el sexto campo e indica la fecha y hora en que el contenido del archivo se modificó por última vez.

---

### Nombre del archivo

Es el ultimo campo y contiene el nombre del archivo o directorio

---

## Ordenar Archivos

Por defecto, el resultado del comando ls está ordenado alfabéticamente según el nombre del archivo. Pero también se puede ordenar usando otros método.

Los tipos de ordenamientos son los siguientes:

- **-t** : La opción -t ordenará los archivos por su sello de tiempo (timestamp)

- **-S** : La opción -S (size) ordenará los archivos por tamaño de archivo:

- **-r** : La opción -r (reverse) invertirá el orden de cualquier tipo de ordenación. 





