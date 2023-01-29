# Subqueries 

Un subquery es una consulta SQL anidada dentro de otra consulta. Es decir, es una consulta dentro de otra consulta. Un subquery se ejecuta primero y su resultado se utiliza como uno de los inputs para la consulta principal. Los subqueries se utilizan para filtrar resultados, crear conjuntos de datos complejos y para unir tablas de manera dinámica. Los subqueries se escriben entre paréntesis y se pueden utilizar en varias partes de una consulta, tales como en la cláusula SELECT, FROM, WHERE, HAVING entre otros.

## Subquery en el SELECT

```sql
SELECT nombre, (SELECT SUM(salario) FROM empleados WHERE departamento = 'Ventas') AS salario_total
FROM departamentos;
```

En este ejemplo, el subquery se encuentra dentro de la cláusula SELECT y se utiliza para calcular el salario total de todos los empleados del departamento de ventas y mostrarlo junto con el nombre del departamento.

## Subquery en el FROM

```sql
SELECT * FROM ( 
    SELECT 
    `dept_name` AS 'departamento', 
    ROUND(AVG(`S`.`salary`), 2) AS 'promedio' 
    FROM `departments` `D`  
    INNER JOIN `dept_emp` `DE` ON `D`.`dept_no` = `DE`.`dept_no` 
    INNER JOIN `employees` `E` ON `E`.`emp_no` = `DE`.`emp_no` 
    INNER JOIN `salaries` `S` ON `S`.`emp_no` = `E`.`emp_no` 
    WHERE `S`.`to_date` > NOW() 
    GROUP BY `D`.`dept_name` 
    ) AS `SQ` 
WHERE `SQ`.`promedio` > 40000;
```

un subquery en un from serviria como si estuvieras consultado una tabla


## Subquery en el WHERE

```sql
SELECT * 
FROM empleados
WHERE salario > (SELECT AVG(salario) FROM empleados);
```

En este ejemplo, el subquery se encuentra dentro de la cláusula WHERE y se utiliza para obtener el salario promedio de todos los empleados y utilizarlo para filtrar los empleados que tienen un salario mayor al promedio.


## Subquery en el HAVING

```sql
SELECT departamento, COUNT(*)
FROM empleados
GROUP BY departamento
HAVING COUNT(*) > (SELECT AVG(empleados_por_departamento) FROM (SELECT COUNT(*) as empleados_por_departamento FROM empleados GROUP BY departamento));
```

En este ejemplo, el subquery se encuentra dentro de la cláusula HAVING y se utiliza para obtener el promedio de empleados por departamento y utilizarlo para filtrar los departamentos que tienen un número de empleados mayor al promedio.