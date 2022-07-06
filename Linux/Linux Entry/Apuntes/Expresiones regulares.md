# Expresiones regulares

Las expresiones regulares tienen dos formas comunes: la forma básica y la forma extendida. La mayoría de los comandos que utilizan expresiones regulares pueden interpretar expresiones regulares básicas. Sin embargo, las expresiones regulares extendidas no están disponibles para todos los comandos y normalmente requieren una opción de comando para funcionar correctamente.


En la siguiente tabla se resumen los caracteres básicos de las expresiones regulares:


|Caracteres Básicos Regex	|Significado|
|-|-|
|.	|Cualquier carácter individual|
|[ ]	|Cualquier carácter especificado|
|[^]	|Cualquier carácter que no es el carácter especificado|
|*	|Cero o más del carácter anterior|
|^	|Si es el primer carácter del patrón, el patrón deberá estar al principio de la línea para coincidir, si no es así se tratará como un ^ literal.|
|$	|Si es el último carácter del patrón, el patrón deberá estar al final de la línea para coincidir, si no es así se tratará como un $ literal.|


En la siguiente tabla se resumen las expresiones regulares extendidas, que se deben utilizar con el comando egrep o la opción -E con el comando grep:

|Caracteres Básicos Regex	|Significado|
|-|-|
|+	|Uno o más del patrón anterior|
|?	|El patrón es opcional|
|{ }|	Especificar mínimo, máximo, o coincidencias exactas en el patrón anterior|
| \|	|Alternancia - el “o” lógico|
|( )	|Se usa para crear grupos|}

> **Note**
> Solamente veremos expresiones regulares basicas, para mas informacion de expresiones regulares extendidas, consulte Linux Essentials

## Patrones básicos

Las expresiones regulares son patrones que sólo ciertos comandos pueden interpretar. Las expresiones regulares se pueden expandir para que coincidan con ciertas secuencias de caracteres en el texto. 

Veamos algunos ejemplos:

### Caracteres de Anclaje

Los caracteres de anclaje son una de las formas con que se pueden utilizar expresiones regulares para limitar los resultados de una búsqueda. 

> **Warning**
> Para evitar que el shell los malinterprete como caracteres especiales del shell, estos patrones deben escribirse protegidos por comillas sólidas, lo que simplemente significa colocarlos entre comillas.

```terminal
$ grep 'root' passwd
```

El primer carácter de anclaje ^ se utiliza para indicar que el patrón debe aparecer al principio de la línea.

```terminal
$ grep '^root' /etc/passwd
```

El segundo carácter de anclaje $ se puede utilizar para indicar que el patrón debe aparecer al final de la línea, reduciendo eficazmente los resultados de la búsqueda. 

```terminal
$ grep 'r$' alpha-first.txt
```
> **Warning**
> Una vez más, la posición de este carácter es importante; el $ debe ser el último carácter en el patrón para ser eficaz como anclaje.

---

### Encontrar caracteres coincidentes usando .

Una de las expresiones más útiles es el carácter . (punto). Representa cualquier carácter excepto el carácter de nueva línea. 

```terminal
$ grep 'r..t' paaswd.txt
```

---

### Encontrar un carácter único usando []

Los corchetes [ ] se utilizan para indicar caracteres únicos o rangos de caracteres posibles en una lista.

Para encontrar todas las líneas en un archivo que contienen un número, utilizariamos el patrón [0123456789] o [0-9]

```terminal
$ grep '[0-9]' texto.txt
```

Por otro lado, para encontrar todas las líneas que contienen caracteres no numéricos, se inserta un ^ como primer carácter dentro de los corchetes. Este carácter niega los caracteres que lo siguen:


```terminal
$ grep '[^0-9]' texto.txt
```

Cuando otros caracteres de expresión regular se colocan dentro de corchetes, se tratan como caracteres literales. Por ejemplo, el carácter . normalmente indica cualquier carácter. Pero si se coloca dentro de corchetes simplemente se referirá al carácter . (punto). 


```terminal
$ grep '[.]' profile.txt
```

---

### Indicar un carácter o patrón repetido utilizando el *

El carácter de expresión regular * se utiliza para indicar la ausencia o la presencia una o más veces del carácter o patrón que lo precede. Por ejemplo, e* indicaría la ausencia (cero) o la presencia, una o más veces, de la letra e:

```terminal
$ grep 're*d' texto.txt
```

También es posible indicar la ausencia o presencia una o más veces de una lista de caracteres utilizando los corchetes. El patrón [oe]* se refiere a líneas con ausencia o presencia una o más veces del carácter o o del carácter e


```terminal
$ grep 'r[oe]*d' texto.txt
```

--- 

### Entrada estándar

Si no se proporciona un nombre de archivo, el comando grep actuará sobre la entrada estándar, que normalmente proviene del teclado y de la entrada proporcionada por el usuario que está ejecutando el comando. Esto permite que el uso de grep se convierta en una experiencia interactiva donde el usuario escribe y grep filtra la entrada a medida que avanza. 

```terminal
$ grep 'red'
```

> **Note**
> presione Ctrl+D cuando esté listo para volver al intérprete de comandos (prompt).




