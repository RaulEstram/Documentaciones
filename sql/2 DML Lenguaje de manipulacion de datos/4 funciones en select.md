# Funciones

las funciones son una forma de procesar o transformar datos en una consulta SQL. Algunas de las funciones más comunes en MySQL son:

* `COUNT()`: Devuelve el número de filas en una tabla o el número de veces que aparece un valor específico en una columna. Ejemplo: `SELECT COUNT(*) FROM table`
* `SUM()`: Devuelve la suma de los valores en una columna. Ejemplo: `SELECT SUM(col) FROM table`
* `AVG()`: Devuelve el promedio de los valores en una columna. Ejemplo: `SELECT AVG(col) FROM table`
* `MIN()`: Devuelve el valor mínimo en una columna. Ejemplo: `SELECT MIN(col) FROM table`
* `MAX()`: Devuelve el valor máximo en una columna. Ejemplo: `SELECT MAX(col) FROM table`
* `UPPER()`: Convierte una cadena a mayúsculas. Ejemplo: `SELECT UPPER(col) FROM table`
* `LOWER()`: Convierte una cadena a minúsculas. Ejemplo: `SELECT LOWER(col) FROM table`
* `LENGTH()`: Devuelve la longitud de una cadena. Ejemplo: `SELECT LENGTH(col) FROM table`
* `CONCAT()`: Concatena dos o más cadenas. Ejemplo: `SELECT CONCAT(col1, ' ', col2) FROM table`
* `NOW()`: Devuelve la fecha actual `SELECT * FROM table WHERE date_column > NOW();`.
* `ROUND`: Función para dar formato repecto al redondeo a datos numéricos. Ejemplo: `ROUND(numero[, numero de decimales])`
* `LEFT()`: Función que trabaja con cadenas y extrae el número de caracteres que se indique como parámetro. Ejemplo: `LEFT(codena, numero_de_caracteres)`


Estas funciones son solo algunas de las muchas funciones disponibles en MySQL y en otros sistemas gestores de bases de datos (DBMS). Es importante tener en cuenta que no todas las funciones son soportadas por todos los sistemas gestores de bases de datos y algunas de ellas pueden variar en su sintaxis.