## CASE

```sql
SELECT col1, col2, 
       CASE 
           WHEN col3 > 6 THEN 'aprobado' 
           ELSE 'reprobado' 
       END AS resultado
FROM table_name;

```

## IF

```sql
SELECT col1, col2, 
       IF(col3 > 6, 'aprobado', 'reprobado') AS resultado
FROM table_name;
```