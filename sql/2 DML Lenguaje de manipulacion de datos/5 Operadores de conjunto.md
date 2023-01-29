## Operadores de conjunto

los operadores de conjunto son utilizados para trabajar con conjuntos de datos en una consulta SQL. Estos son algunos de los operadores de conjunto más comunes en MySQL:

* `UNION`: Este operador combina los resultados de dos o más consultas y elimina los duplicados. Ejemplo: `SELECT col1, col2 FROM table1 UNION SELECT col1, col2 FROM table2`
* `UNION ALL`: Este operador combina los resultados de dos o más consultas y no elimina los duplicados. Ejemplo: `SELECT col1, col2 FROM table1 UNION ALL SELECT col1, col2 FROM table2`
* `INTERSECT`: Este operador devuelve las filas que son comunes en dos o más consultas. Ejemplo: `SELECT col1, col2 FROM table1 INTERSECT SELECT col1, col2 FROM table2`
* `EXCEPT`: Este operador devuelve las filas de la primera consulta que no están en la segunda consulta. Ejemplo: `SELECT col1, col2 FROM table1 EXCEPT SELECT col1, col2 FROM table2`


## Ejemplos consultas

teniendo en cuenta la siguiente base de datos podremos realizar varias consultas:

![Base de datos employees](https://dev.mysql.com/doc/employee/en/images/employees-schema.png)

* UNION

```sql
select * from departments union select * from departments;
```

```shell
+---------+--------------------+
| dept_no | dept_name          |
+---------+--------------------+
| d009    | Customer Service   |
| d005    | Development        |
| d002    | Finance            |
| d003    | Human Resources    |
| d001    | Marketing          |
| d004    | Production         |
| d006    | Quality Management |
| d008    | Research           |
| d007    | Sales              |
+---------+--------------------+
```


* UNION ALL

```sql
select * from departments union all select * from departments;
```

```shell
+---------+--------------------+
| dept_no | dept_name          |
+---------+--------------------+
| d009    | Customer Service   |
| d005    | Development        |
| d002    | Finance            |
| d003    | Human Resources    |
| d001    | Marketing          |
| d004    | Production         |
| d006    | Quality Management |
| d008    | Research           |
| d007    | Sales              |
| d009    | Customer Service   |
| d005    | Development        |
| d002    | Finance            |
| d003    | Human Resources    |
| d001    | Marketing          |
| d004    | Production         |
| d006    | Quality Management |
| d008    | Research           |
| d007    | Sales              |
+---------+--------------------+
```

* INTERSECT

```sql
SELECT `emp_no` from `salaries` WHERE `to_date` > NOW() INTERSECT SELECT `emp_no` FROM `employees` LIMIT 10;
```

```shell
+--------+
| emp_no |
+--------+
|  10001 |
|  10002 |
|  10003 |
|  10004 |
|  10005 |
|  10006 |
|  10007 |
|  10009 |
|  10010 |
|  10012 |
+--------+
```

* EXCEPT

```sql
SELECT `emp_no` from `dept_emp` WHERE `to_date` < NOW() EXCEPT SELECT `emp_no` FROM `employees` LIMIT 10;
```

```shell
Empty set (0.42 sec)
```
