# Comandos

a continuacion se mostrara una coleccion de comandos en linux







## navegacion

- **ls**: el comando **ls** muestra una lista de información sobre archivos.
    - **-l** : long --> mas informacion
    - **-r** : reverse --> orden inverso al normal
    - **-S** : Size --> ordenar por tamaño
    - **-t** : timestamp --> ordenar por fecha

```Linux
$ ls [Opciones] [Argumento]
```

- **pwd**: El comando **pwd** imprime el directorio de trabajo (print working directory), su ubicación actual dentro del sistema de archivos:

```Linux
$ pwd [Opciones]
```

- **cd**: El comando **cd** (change directory) se utiliza para cambiar de directorio y navegar por la estructura del sistema de archivos.

```Linux
$ cd [Opciones] [ruta]
```













## Permisos

- **chmod** : El comando chmod se utiliza para cambiar los permisos de un archivo o directorio. Sólo el usuario raíz o el usuario propietario del archivo puede cambiar los permisos de un archivo.

```terminal
chmod [<COJUNTO DE PERMISOS><ACCIÓN><PERMISOS>]... ARCHIVO
```












## propietarios archivos

- **chown**: el comando chown permite cambiar el grupo propietario, lo cual puede ser realizado por el usuario root o el propietario del archivo.

    Para cambiar el usuario propietario de un archivo, se puede utilizar la siguiente sintaxis. El primer argumento, [PROPIETARIO], especifica qué usuario debe ser el nuevo propietario. El segundo argumento, ARCHIVO, especifica el archivo al cual se está cambiando el propietario.

```terminal
$ chown [OPCIONES] [PROPIETARIO] ARCHIVO
```















## Visualizacion de archivos

- **cat** : El comando cat mostrará todo el contenido del archivo, por lo que se recomienda principalmente para archivos pequeños para los que el resultado es limitado y no requiere desplazamientos de pantalla. 

```terminal
$ cat [OPCIONES] [ARCHIVO]
```

- **head** y **tail** : Estos comandos se utilizan para ver un número seleccionado de líneas desde la parte superior o inferior de un archivo.
    - **-n** : se utiliza para especificar la cantidad de líneas a mostrar

**head**
```terminal
$ head [OPCIONES] [ARCHIVO]
```
**tail**
```terminal
$ tail [OPCIONES] [ARCHIVO]
```
**-n**
```terminal
$ {head | tail} -n número_de_líneas archivo
```






## Manejo de archivos

- **cp** : El comando cp se utiliza para copiar archivos.

```terminal
$ cp [OPCIONES] ORIGEN DESTINO
```

- **dd** : El comando dd se utiliza para copiar archivos o particiones enteras al nivel de bits.

```terminal
$ dd [OPCIONES] OPERANDO
```

- **mv** : El comando mv se utiliza para mover archivos, requiere al menos dos argumentos: un origen y un destino.a

> El comando mv puede utilizarse para mover varios archivos, siempre y cuando el argumento final proporcionado al comando sea el destino. 

```terminal
$ cp {ORIGEN [ORIGEN2 [ORIGEN3]]} DESTINO
```

- **rm** : El comando rm (remove) se utiliza para eliminar archivos y directorios. 
    - **-r** o **-R** : elimina directorios junto con todos los archivos que tiene dentro
```terminal
$ rm [OPCIONES] ARCHIVO
```

- **grep** : El comando **grep** es un filtro de texto que busca líneas en una entrada y devolverá aquellas que coincidan con un patrón determinado.

```terminal
$ grep [OPCIONES] PATRÓN [ARCHIVO]
```








## Sistema

- **shutdown** : Este comando nos sirve para agabar el sistema de forma segura.

```shell
$ shutdown [OPCIONES] HORA [MENSAJE]
```

- **ifconfig** : El comando ifconfig significa “configuración de interfaz” (interface configuration) y se utiliza para mostrar información sobre la configuración de red.

```shell
$ ifconfig [OPCIONES] 
```

- **iwconfig** : El comando iwconfig es similar al comando ifconfig, pero se refiere a interfaces de redes inalámbricas (wireless).

```shell
$ iwconfig [OPCIONES] 
```

- **passwd** : El comando passwd nos sirve para cambiar la contraseña de los usuarios

```shell
$ passwd [Opciones] [Usuario]
```

Si el usuario desea ver información sobre su contraseña, puede utilizar la opción -S:

```shell
$ passwd -S user
```






## paquetes

- **apt-get** : es para administrar paquetes en nuestro sistema
    Es recomendable realizar el siguiente comando cada vez que se instalara un nuevo paquete:
```shell
$ sudo apt-get update
```

- **apt-cache search** : Nos sirve para buscar paquetes mediante keywords

```shell
$ apt-cache search cow
```

- **apt-get installl** : Nos sirve para instalar nuevos paquetes en nuestro sistema.













## otros random

- **aptitude**: el comando aptitude es una función de gestión de paquetes disponible en algunas versiones de Linux. 












## random/ divertidos

- **sl** : es un comando que hace una animacion de un tren

- **cowsay** : El comando cowsay es una vaca parlante configurable! Use una palabra o frase como argumento.
