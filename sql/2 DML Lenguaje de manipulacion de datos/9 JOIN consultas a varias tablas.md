# JOIN - Hacer consultas a varias tablas.

Los JOIN en MySQL son una manera de combinar datos de varias tablas en una sola consulta. Los tipos de JOIN más comunes en MySQL son:

* `INNER JOIN`: Retorna las filas cuya columna específica en ambas tablas tiene un valor igual. Es decir, solo retorna las filas que tienen una coincidencia en ambas tablas.
* `LEFT JOIN` (o `LEFT OUTER JOIN)`: Retorna todas las filas de la tabla de la izquierda, junto con las filas de la tabla derecha que tienen una coincidencia en la columna específica. Si no hay una coincidencia en la tabla derecha, se retorna un valor NULL para las columnas de la tabla derecha.
* `RIGHT JOIN` (o `RIGHT OUTER JOIN)`: Es similar al LEFT JOIN, pero retorna todas las filas de la tabla derecha, junto con las filas de la tabla izquierda que tienen una coincidencia en la columna específica.
* `FULL OUTER JOIN`: Retorna todas las filas de ambas tablas, junto con las filas que tienen una coincidencia en la columna específica. Si no hay una coincidencia en una de las tablas, se retorna un valor NULL para las columnas de esa tabla.
* `CROSS JOIN`: Retorna el producto cartesiano de ambas tablas, es decir, todas las combinaciones posibles de filas de ambas tablas.
* `SELF JOIN`: Retorna las filas de una tabla en relación consigo misma. Es decir, se utiliza la misma tabla dos veces con nombres diferentes en la consulta.

![tipos de join](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9d/SQL_Joins.svg/2560px-SQL_Joins.svg.png)


