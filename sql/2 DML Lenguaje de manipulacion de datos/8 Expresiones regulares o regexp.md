# Expresiones regulares

Las expresiones regulares son un tipo de patrón que se utilizan para buscar y comparar cadenas de texto en MySQL. Estas expresiones se construyen utilizando caracteres especiales, los cuales representan conjuntos de caracteres, como letras, números o símbolos. Algunos de los operadores más comunes que se utilizan en las expresiones regulares de MySQL son:

* `.`: Cualquier carácter.
* `*`: Cualquier cantidad de caracteres, incluyendo cero.
* `+`: Al menos un carácter.
* `?`: Cero o un carácter.
* `[ ]`: Conjunto de caracteres permitidos.
* `[^ ]`: Conjunto de caracteres prohibidos.
* `^`: El principio de la línea.
* `$`: El final de la línea.
* `{n}`: Exactamente n repeticiones.
* `{n,}`: Al menos n repeticiones.
* `{n,m}`: Entre n y m repeticiones.
* `[cahr1-char2]`: Coincide con cualquier carácter entre el rango dado
* `|` Separa dos patrones de cadena y coincide cada uno.

En MySQL, las expresiones regulares se utilizan en funciones y operadores específicos, como REGEXP, RLIKE y NOT REGEXP/RLIKE, para comparar y buscar patrones en las columnas de una tabla.

* regexp sirve para evaluar las expresiones regulares
* like sirve para usar los comodines `%` y `_`, donde `%` es para cualquier caracter y cuantos sean mientras que `_` es para un solo caracter.