# Permisos

Los permisos determinan la forma en que los diferentes usuarios pueden interactuar con un archivo o directorio. Al enumerar un archivo con el comando **ls -l**, el resultado incluye información sobre sus permisos.

Para ver los permisos, tendremos como referencia el siguiente archivo:

```terminal
-rw-r--r-- 1 sysadmin sysadmin 647 Dec 20  2017 hello.sh
```

## Permisos
Después del carácter de tipo de archivo, se muestran los permisos. Los permisos se dividen en tres grupos de tres caracteres:



### Propietario

El primer grupo se refiere al usuario que posee el archivo. Si su cuenta actual es la propietaria del archivo, se usará el primer grupo de permisos y los demás permisos no tendrán efecto.

---

### Grupo

El segundo conjunto se refiere al grupo que posee el archivo. Si su cuenta actual no es la del propietario del archivo pero es miembro del grupo que posee el archivo, se aplicarán los permisos del grupo y los demás permisos no tendrán efecto.

---

### otros

El último grupo es para todos los demás, cualquiera a quien los dos primeros conjuntos de permisos no sean aplicables. Si no es el usuario que posee el archivo o un miembro del grupo que posee el archivo, se le aplicará el tercer conjunto de permisos.

---

## Tipos de permisos

Un archivo o directorio puede presentar tres permisos diferentes: leer, escribir y ejecutar. La forma en que se aplican estos permisos difiere entre archivos y directorios, como se muestra en la tabla siguiente:

| Permiso | Efectos sobre los Archivos | Efectos sobre los directorios |
| - | - | - |
| leer (read) (r)	| Permite que el contenido del archivo sea leído o copiado.	|Sin el permiso para ejecutar, permite obtener un listado poco detallado de los archivos que contiene el directorio. Con el permiso para ejecutar, **ls -l** proporciona un listado detallado de archivos.|
| escribir (write) (w)	|Permite modificar o reescribir el contenido del archivo. Permite añadir o eliminar archivos en un directorio. | Para que este permiso funcione, el directorio debe tener permiso para ejecutar.|
|ejecutar (execute) (x)|	Permite que un archivo funcione como un proceso, aunque archivos script también requerirán el permiso leer (read).	|Permite que el usuario se traslade del directorio si en el directorio padre también posee permiso escribir (write).|







