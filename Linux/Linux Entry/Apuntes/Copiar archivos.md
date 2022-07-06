# Copiar archivos

Crear copias de archivos puede ser útil por numerosas razones:

- Si se ha creado una copia del archivo antes de que se hayan realizado cambios, siempre podremos revertir al archivo original.
- La copia de un archivo puede utilizarse para transferirlo a un dispositivo extraíble.
- La copia de un documento puede utilizarse como plantilla para un documento nuevo.

```terminal
$ cp [OPCIONES] ORIGEN DESTINO
```

El comando **cp** se utiliza para copiar archivos. Similar al comando mv, requiere al menos dos argumentos: un origen y un destino. 

> Para copiar un archivo, es necesario tener permiso de ejecución para acceder al directorio donde se encuentra el archivo y permiso de lectura para el archivo que se está copiando.

> :warning: También es necesario tener permiso de escritura y ejecución en el directorio al que se está copiando el archivo.


## Comando dd

El comando dd se utiliza para copiar archivos o particiones enteras al nivel de bits.

```terminal
$ dd [OPCIONES] OPERANDO
```

Este comando tiene varias características útiles, entre las que se incluyen:

- Se puede usar para clonar o eliminar (wipe) discos o particiones enteras.
- Se puede usar para copiar datos no procesados (raw) a dispositivos extraíbles como dispositivos USB o CD ROMS.
- Se puede usar para realizar una copia de reserva (backup) y restituir el MBR (Master Boot Record).
- Se puede usar para crear un archivo de un tamaño específico lleno de ceros binarios, el cual puede utilizarse como archivo de intercambio (swap file) (memoria virtual).

Examinemos el siguiente ejemplo. El comando dd creará un archivo denominado /tmp/swapex con 50 bloques de ceros de un megabyte de tamaño:

```terminal
$ dd if=/dev/zero of=/tmp/swapex bs=1M count=50 
```

El comando dd utiliza argumentos especiales para especificar cómo funcionará. A continuación se muestran algunos de los argumentos más utilizados:


|Argumento	|Descripción|
|-|-|
|if|	Archivo de entrada (Input File): El archivo de entrada que se va a leer. ``` $ dd if=/dev/zero of=/tmp/swapex bs=1M count=50 ``` El ejemplo lee el archivo /dev/zero, un archivo especial que contiene un número ilimitado de ceros.|
|of|Archivo de salida (Output File): El archivo de salida que se va a escribir.``` dd if=/dev/zero of=/tmp/swapex bs=1M count=50```|
|bs|Tamaño de bloque (Block Size): El tamaño de bloque que se va a utilizar. De forma predeterminada, el valor se presenta en bytes. Utilice los sufijos siguientes para especificar otras unidades: K, M, G y T para kilobytes, megabytes, gigabytes y terabytes respectivamente. ```dd if=/dev/zero of=/tmp/swapex bs=1M count=50``` En el ejemplo se utiliza un tamaño de bloque de un megabyte.|
|count|Recuento: El número de bloques que se van a leer desde el archivo de entrada. ```dd if=/dev/zero of=/tmp/swapex bs=1M count=50``` En este ejemplo se leen 50 bloques.

