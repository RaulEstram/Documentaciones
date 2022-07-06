# Cambiar los permisos de los archivos

El comando **chmod** se utiliza para cambiar los permisos de un archivo o directorio. Sólo el usuario raíz o el usuario propietario del archivo puede cambiar los permisos de un archivo.

> chmod realmente significa cambiar los modos de acceso (change access mode).


Hay dos métodos para cambiar permisos usando el comando chmod: el método simbólico y el método octal.


El método simbólico es útil para cambiar un conjunto de permisos a la misma vez. El método octal o numérico requiere conocer el valor octal de cada uno de los permisos y requiere que los tres conjuntos de permisos (usuario, grupo, otros) se especifiquen cada vez. Para simplificar las cosas, solamente trataremos el método simbólico. 

## El metodo simbolico

```terminal
chmod [<COJUNTO DE PERMISOS><ACCIÓN><PERMISOS>]... ARCHIVO
```

Para usar el método simbólico de chmod se deben de indicar:

- Conjunto de permisos
- accion
- permisos

---

### Conjunto de permisos

|Símbolo	|Significado|
|-|-|
|u	|Usuario: El usuario propietario del archivo.|
|g	|Grupo: El grupo propietario del archivo.|
|o	|Otros: Cualquier otro que no sea el usuario propietario o un miembro del grupo propietario.|
|a	|Todos: Se refiere al usuario, grupo, y todos los demás.|

### Accion

|Símbolo	|Significado|
|-|-|
|+	|Añadir permiso, si es necesario|
|=	|Especificar el permiso exacto|
|-	|Eliminar el permiso, si es necesario|

### Permisos

|Símbolo|	Significado|
|-|-|
|r	|leer (read)|
|w	|escribir (write)|
|x|	ejecutar (execute)|

---

Finalmente, añada un espacio y los nombres de ruta para los archivos a los que quiere asignar los permisos.


