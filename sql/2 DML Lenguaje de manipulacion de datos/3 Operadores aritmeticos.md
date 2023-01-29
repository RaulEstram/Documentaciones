# Operadores Aritmeticos

MySQL soporta varios operadores aritméticos que se pueden utilizar en consultas SQL para realizar operaciones matemáticas en las columnas de una tabla. Algunos de los operadores aritméticos más comunes son:

* `+`: Suma dos números. Ejemplo: `SELECT col1 + col2 FROM table`
* `-`: Resta dos números. Ejemplo: `SELECT col1 - col2 FROM table`
* `*`: Multiplica dos números. Ejemplo: `SELECT col1 * col2 FROM table`
* `/`: Divide dos números. Ejemplo: `SELECT col1 / col2 FROM table`
* `%`: Devuelve el resto de la división de dos números. Ejemplo: `SELECT col1 % col2 FROM table`


También se pueden utilizar estos operadores con números constantes. Por ejemplo:


```sql
SELECT col1 + 5 FROM table
```

Además, MySQL también soporta operadores aritméticos avanzados como potenciación y raíz cuadrada. Ejemplo:

```sql
SELECT POWER(col1,2) FROM table
```

```sql
SELECT SQRT(col1) FROM table
```

> **Note**Es importante tener en cuenta que estos operadores solo pueden ser aplicados a columnas de tipo numérico.