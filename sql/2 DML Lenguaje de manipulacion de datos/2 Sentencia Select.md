# Uso del select

Una instrucción select nos sirve para extraer información d euna o más tablas de una base de datos.

## Sintaxis basica

```sql
SELECT [DISTINCT | ALL] {column1, column2, ... | * }
FROM table1 [AS alias1]
[JOIN table2 [AS alias2] ON join_condition]
[WHERE condition1]
[GROUP BY column1, column2, ...
[HAVING condition2]]
[ORDER BY column1 [ASC | DESC], column2 [ASC | DESC], ...]
[LIMIT number [OFFSET offset]];
```

* `SELECT` es la cláusula principal de la instrucción y indica que se están seleccionando datos de una tabla.
* `DISTINCT | ALL` es opcional y se utiliza para especificar si se deben eliminar o no los duplicados en los resultados.
* `column1, column2, ...` son los nombres de las columnas que se desean seleccionar o `*` por si se desea seleccionar todas las columnas.
* `FROM` indica de qué tabla se desean seleccionar los datos.
* `AS alias1` es opcional y se utiliza para asignar un alias a una tabla.
* `JOIN` es opcional y se utiliza para unir dos o más tablas en base a una condición de unión.
* `ON join_condition` es opcional y se utiliza para especificar la condición de unión entre las tablas.
* `WHERE` es opcional y se utiliza para filtrar los resultados de la consulta según una condición específica.
* `GROUP BY` es opcional y se utiliza para agrupar los resultados según una o varias columnas.
* `HAVING` es opcional y se utiliza para filtrar los resultados de una consulta agrupada según una condición específica.
* `ORDER BY` es opcional y se utiliza para ordenar los resultados según una o varias columnas.
* `LIMIT` es opcional y se utiliza para limitar el número de filas en los resultados de una consulta.
* `OFFSET` offset es opcional y se utiliza para especificar a partir de qué fila se deben comenzar a recuperar los resultados de una consulta.

> **Note** Hay que tener en cuenta que esta es solo una forma genérica de una sentencia SELECT, puede variar dependiendo del sistema gestor de base de datos que utilice.

## Ejemplos consultas

teniendo en cuenta la siguiente base de datos podremos realizar varias consultas:

[![Base de datos employees](Base de datos employees "Base de datos employees")](https://dev.mysql.com/doc/employee/en/images/employees-schema.png "Base de datos employees")