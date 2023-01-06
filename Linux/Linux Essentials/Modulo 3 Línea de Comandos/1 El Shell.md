# El Shell

Un shell es el intérprete que traduce los comandos introducidos por un usuario en acciones a realizar por el sistema operativo. 

El shell más comúnmente utilizado para las distribuciones de Linux se llama el BASH shell. 

El BASH shell tiene también otras funciones populares:

* **Scripting**: La capacidad de colocar los comandos en un archivo y ejecutar el archivo, resultando en todos los comandos siendo ejecutados. Esta función también tiene algunas características de programación, tales como las instrucciones condicionales y la habilidad de crear funciones (AKA, subrutinas).
* **Los Alias**: La habilidad de crear "nicknames" (o «sobrenombres» en español) cortos para más comandos más largos.
* **Las Variables**: Las Variables se utilizan para almacenar información para el BASH shell. Estas variables pueden utilizarse para modificar cómo las funciones y los comandos trabajan y proporcionan información vital sobre el sistema.

## Prompt

La estructura del prompt puede variar entre las distribuciones, pero por lo general contiene información sobre el usuario y el sistema. A continuación te mostramos una estructura común de un prompt:

```shell
sysadmin@localhost:~$
```

El prompt anterior proporciona el nombre del usuario registrado en (sysadmin), el nombre del sistema (localhost) y el directorio actual (~). El símbolo ~ se utiliza como abreviación para el directorio principal del usuario (el directorio principal del usuario viene bajo el directorio /home (o «inicio» en español) y con el nombre de la cuenta de usuario, por ejemplo: /home/sysadmin).

## Los Comandos de Formato

Muchos comandos se pueden utilizar por sí mismos sin más entradas. Algunos comandos requieren entradas adicionales para funcionar correctamente. Esta entrada adicional viene en dos formas: opciones y argumentos. 

El formato típico de un comando es el siguiente:

```shell
comando [opciones] [argumentos]
```

Las opciones se utilizan para modificar el comportamiento básico de un comando y los argumentos se utilizan para proporcionar información adicional (tal como un nombre de archivo o un nombre de usuario). Cada opción y argumento vienen normalmente separados por un espacio, aunque las opciones pueden a menudo ser combinadas.

### Trabajando con las Opciones

Las opciones son a menudo de una letra; sin embargo, a veces serán "palabras". 

Por ejemplo, puedes utilizar la opción `-l` con el comando `ls` para ver más información sobre los archivos que se listan.

```shell
sysadmin@localhost:~$ ls -l   
```

En la mayoría de los casos, las opciones pueden utilizarse conjuntamente con otras opciones. Por ejemplo, los comandos `ls -l -h` o `ls -lh` listarán los archivos con sus detalles, pero se mostrará el tamaño de los archivos en formato de legibilidad humana en lugar del valor predeterminado (bytes):

```shell
sysadmin@localhost:~$ ls -lh   
```

> **Note** Nota que el ejemplo anterior también demostró cómo se pueden combinar opciones de una letra: -lh . El orden de las opciones combinadas no es importante.

## History

Al ejecutar un comando en una terminal, el comando se almacena en **"history list"**. Esto está diseñado para que más adelante puedas ejecutar el mismo comando más fácilmente puesto que no necesitarás volver a introducir el comando entero. 

Para ver la lista de historial de una terminal, utiliza el comando `history`

```shell
sysadmin@localhost:~$ history  
```

Si ves un comando que quieres ejecutar en la lista que haya generado el comando history, puedes ejecutar este comando introduciendo el signo de exclamación y luego el número al lado del comando, por ejemplo:

```shell
sysadmin@localhost:~$ history                                     
    1  date                                                      
    2  ls                                                         
    3  cal 5 2015                                                 
    4  history                                                    
sysadmin@localhost:~$ !3                                        
cal 5 2015                                                        
     May 2015                                                     
Su Mo Tu We Th Fr Sa                                              
                1  2                                              
 3  4  5  6  7  8  9                                             
10 11 12 13 14 15 16                                              
17 18 19 20 21 22 23                                            
24 25 26 27 28 29 30                                               
                  31                                              
sysadmin@localhost:~$

```

ejemplos de **opciones** del comando **history**

| Ejemplo  |  Significado |
| ------------ | ------------ |
| history 5  | Muestra los últimos cinco comandos de la lista del historial  |
| !!  | Ejecuta el último comando otra vez  |
|  !-5 |  Ejecuta el quinto comando desde la parte inferior de la lista de historial |
|  !ls | Ejecuta el comando ls más reciente  |
