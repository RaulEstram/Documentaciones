# Parametros u opciones de la clausula WHERE

La cláusula `WHERE` en MySQL se utiliza para filtrar los resultados de una consulta según una condición específica. Los parámetros o opciones que se pueden usar junto con `WHERE` son:


* **Operadores de comparación**: =, <>, <, >, <=, >=, LIKE, IN, BETWEEN, IS NULL, IS NOT NULL
* **Operadores lógicos**: AND, OR, NOT
* **Operadores de comparacion subconsulta**: IN, ANY, ALL, SOME
* **Funciones**: COUNT, SUM, AVG, MIN, MAX, UPPER, LOWER, LENGTH, ROUND, NOW(), CURDATE(), CURTIME()


Un mini ejemplo seria: 

```sql
SELECT first_name, last_name, salary
FROM employees
WHERE salary > 50000 AND (department = 'IT' OR department = 'HR');
```

> **Note** Es importante tener en cuenta que los parámetros y opciones disponibles en una cláusula WHERE pueden variar dependiendo del sistema gestor de bases de datos que se esté utilizando.


## Operadores de comparacion

Los operadores de comparación se utilizan para comparar valores en una cláusula WHERE y devolver un valor verdadero o falso. Estos son los operadores de comparación más comunes en MySQL:

* `=`: Igual a. Este operador se utiliza para comparar si dos valores son iguales. Ejemplo: `WHERE salary = 50000`
* `<>` o `!=`: Diferente de. Este operador se utiliza para comparar si dos valores son diferentes. Ejemplo: `WHERE department <> 'IT'`
* `<`: Menor que. Este operador se utiliza para comparar si un valor es menor que otro. Ejemplo: `WHERE age < 30`
* `>`: Mayor que. Este operador se utiliza para comparar si un valor es mayor que otro. Ejemplo: `WHERE salary > 50000`
* `<=`: Menor o igual a. Este operador se utiliza para comparar si un valor es menor o igual a otro. Ejemplo: `WHERE age <= 30`
* `>=`: Mayor o igual a. Este operador se utiliza para comparar si un valor es mayor o igual a otro. Ejemplo: `WHERE salary >= 50000`
* `LIKE`: Similar a. Este operador se utiliza para comparar si un valor es similar a otro utilizando un patrón. Ejemplo: `WHERE first_name LIKE 'J%'`, utiliza "%" para todos los caracteres y cuandos sean y "_" para cualquier caracter pero que sea solamente uno.
* `[NOT] IN`: En. Este operador se utiliza para comparar si un valor está dentro de un conjunto de valores específico. Ejemplo: `WHERE department IN ('IT', 'HR')`, tambien se pueden utilizar subqueries con este operador.
* `BETWEEN`: Entre. Este operador se utiliza para comparar si un valor está entre dos valores específicos. Ejemplo: `WHERE salary BETWEEN 40000 AND 60000`
* `IS NULL`: Es nulo. Este operador se utiliza para comparar si un valor es nulo. Ejemplo: `WHERE middle_name IS NULL`
* `IS NOT NULL`: No es nulo. Este operador se utiliza para comparar si un valor no es nulo. Ejemplo: `WHERE middle_name IS NOT NULL`

> **Note** Es importante tener en cuenta que cada Sistema Gestor de Base de Datos (DBMS) puede tener sus propios operadores y funciones, y algunos pueden variar en su sintaxis.

## Operadores lógicos

los operadores lógicos se utilizan para combinar múltiples condiciones en una cláusula WHERE. Estos son los operadores lógicos más comunes en MySQL:

* `AND`: Y. Este operador combina dos o más condiciones y devuelve verdadero si todas las condiciones son verdaderas. Ejemplo: `WHERE salary > 50000 AND department = 'IT'`
* `OR`: O. Este operador combina dos o más condiciones y devuelve verdadero si al menos una de las condiciones es verdadera. Ejemplo: `WHERE salary > 50000 OR department = 'HR'`
* `NOT`: No. Este operador niega una condición y devuelve verdadero si la condición es falsa. Ejemplo: `WHERE NOT salary > 50000`

**También es posible utilizar paréntesis para agrupar condiciones** y controlar el orden de evaluación de las mismas. Por ejemplo, `WHERE (salary > 50000 AND department = 'IT') OR (age < 30 AND department = 'HR')`

## Operadores de comparacion subconsulta

los operadores `IN`, `ANY`, `ALL` y `SOME` son utilizados para comparar una columna a un conjunto de valores o a otra consulta en una cláusula WHERE. Estos son los operadores más comunes:

* `[NOT] IN`: Este operador compara una columna a un conjunto de valores especificados. Ejemplo: `SELECT * FROM table WHERE col IN (1, 2, 3)`
* `ANY`: Este operador compara una columna a los resultados de otra subconsulta. Ejemplo: `SELECT * FROM table1 WHERE col = ANY (SELECT col FROM table2)`
* `ALL`: Este operador compara una columna a los resultados de otra subconsulta y devuelve verdadero si todos los valores en la subconsulta cumplen la condición. Ejemplo: `SELECT * FROM table1 WHERE col < ALL (SELECT col FROM table2)`
* `SOME`: Este operador es similar al operador ANY y se utiliza de la misma manera, pero algunos sistemas gestores de bases de datos (DBMS) pueden soportar solo uno de los dos.

> **Note** Practicamente son utilizados para subqueries