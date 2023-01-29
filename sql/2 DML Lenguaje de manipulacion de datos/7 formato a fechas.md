# Formato a fechas

MySQL proporciona varias funciones para dar formato a las fechas. Algunas de las funciones más comunes son:


* `DATE_FORMAT(date, format)`: Devuelve una fecha en el formato especificado. El primer argumento es la columna de fecha y el segundo argumento es el formato deseado. Ejemplo:

```sql
SELECT DATE_FORMAT(date_column, '%Y-%m-%d') FROM table
```

* `DATE_ADD(date, INTERVAL value type)`: Añade un intervalo de tiempo a una fecha. El primer argumento es la columna de fecha y el segundo argumento es el intervalo de tiempo a añadir. El tercer argumento es el tipo de intervalo, que puede ser **DAY, MONTH, YEAR, HOUR, MINUTE**, etc. Ejemplo:

```sql
SELECT DATE_ADD(date_column, INTERVAL 3 DAY) FROM table
```

* `DATE_SUB(date, INTERVAL value type)`: Resta un intervalo de tiempo a una fecha. El primer argumento es la columna de fecha y el segundo argumento es el intervalo de tiempo a restar. El tercer argumento es el tipo de intervalo, que puede ser DAY, MONTH, YEAR, HOUR, MINUTE, etc. Ejemplo:

```sql
SELECT DATE_SUB(date_column, INTERVAL 1 MONTH) FROM table
```

* `EXTRACT(unit FROM date)`: Devuelve un componente específico de una fecha. El primer argumento es el componente de la fecha y el segundo argumento es la columna de fecha. Los componentes soportados son: DAY, MONTH, YEAR, HOUR, MINUTE, etc. Ejemplo:

```sql
SELECT EXTRACT(MONTH FROM date_column) FROM table
```

* `NOW()`: Devuelve la fecha y hora actual en formato "aaaa-mm-dd hh:mm:ss".
* `CURDATE()`: Devuelve la fecha actual en formato "aaaa-mm-dd"
* `CURTIME()`: Devuelve la hora actual en formato "hh:mm:ss"

## Formatos para DATE_FORMAT

La función DATE_FORMAT en MySQL utiliza una serie de especificadores de formato para especificar cómo se debe formatear una fecha. Algunos de los especificadores de formato más comunes son:

* `%Y`: Año en formato de cuatro dígitos, como "2022"
* `%y`: Año en formato de dos dígitos, como "22"
* `%m`: Mes en formato numérico, con dos dígitos, como "01" para enero o "12" para diciembre.
* `%c`: Mes en formato numérico, sin ceros iniciales, como "1" para enero o "12" para diciembre.
* `%D`: Representación de la fecha con el formato "%m/%d/%y"
* `%d`: Día del mes en formato numérico, con dos dígitos, como "01" o "31"
* `%e`: Día del mes en formato numérico, sin ceros iniciales, como "1" o "31"
* `%j`: Día del año en formato numérico, como "001" para el primer día del año o "365" para el último día del año
* `%H`: Hora en formato de 24 horas, con dos dígitos, como "09" o "22"
* `%h`: Hora en formato de 12 horas, con dos dígitos, como "09" o "10"
* `%i`: Minutos con dos dígitos, como "05" o "59"
* `%s`: Segundos con dos dígitos, como "05" o "59"
* `%U`: Semana del año en formato numérico, comenzando en el primer lunes como la primera semana
* `%u`: Semana del año en formato numérico, comenzando en el primer domingo como la primera semana
* `%W`: Nombre de la semana completa, como "Monday" o "Sunday"
* `%w`: Día de la semana en formato numérico, comenzando con el domingo como día 0 y el sábado como día 6