# Trabajarndo con tablas

## Creando tablas

Para crear una tabla en MySQL, puedes utilizar el comando CREATE TABLE. Este comando requiere especificar el nombre de la tabla y los campos (columnas) que tendrá, junto con sus tipos de datos y cualquier restricción o opción adicional. Ejemplo:

```sql
CREATE TABLE [IF NOT EXISTS] [dbNombre.]nombre_tabla (
    campo1 tipo_de_dato [opciones],
    campo2 tipo_de_dato [opciones],
    campo3 tipo_de_dato [opciones],
    ...
    [constraints de la tabla]
    PRIMARY KEY (campo1, campo2)
);
```

Por ejemplo, si quieres crear una tabla llamada "clientes" con los campos "id", "nombre", "apellido" y "fecha_nacimiento" con tipos de datos respectivamente INT, VARCHAR, VARCHAR y DATE, la sentencia sería:

```sql
CREATE TABLE clientes (
    id INT NOT NULL AUTO_INCREMENT,
    nombre VARCHAR(50) NOT NULL,
    apellido VARCHAR(50) NOT NULL,
    fecha_nacimiento DATE NOT NULL,
    PRIMARY KEY (id)
);
```

En este ejemplo, se estableció el campo "id" como clave primaria, y se estableció que no pueden tener valores nulos.

Es importante que revises la sintaxis de SQL y los tipos de datos soportados por MySQL, para poder crear tablas adecuadas.

## Atributos u opciones de columnas mas comunes

| Atributo u opcion  |  descripcion |
| ------------ | ------------ |
| NOT NULL  | indica que una columna no puede tener un valor nulo.  |
| UNIQUE  |  indica que los valores en una columna deben ser únicos. |
| PRIMARY KEY  | indica que una columna o un conjunto de columnas es la clave principal de la tabla y que los valores deben ser únicos e irrepetibles.  |
| FOREIGN KEY  | indica que una columna es una clave externa y establece una relación con otra tabla.  |
| DEFAULT  |  establece un valor predeterminado para una columna |
| AUTO_INCREMENT  | indica que una columna debe ser autoincrementable.  |
| COMMENT  | permite agregar un comentario a una columna.  |

## Creando tablas temporales

Una tabla temporal es una tabla especial en MySQL que se utiliza para almacenar datos temporalmente. Las tablas temporales son muy útiles en situaciones en las que se necesita una tabla temporal para una tarea específica, pero no se requiere que los datos se almacenen de forma permanente.

Para crear una tabla temporal en MySQL, se utiliza la sintaxis de CREATE TEMPORARY TABLE.

Aquí hay un ejemplo de cómo crear una tabla temporal llamada "temp_orders":

```sql
CREATE TEMPORARY TABLE temp_orders (
    order_id INT,
    customer_name VARCHAR(255),
    order_total DECIMAL(10,2)
);
```

> *Note* Es importante tener en cuenta que las tablas temporales solo están disponibles para la sesión actual, una vez que se cierra la conexión o se finaliza la sesión, los datos almacenados en la tabla temporal se pierden.

## Creando una tabla a partir de otra (puede pasarle todos los datos)

Si queremos crear una tabla que sea igual a otra y que tenaga los mismos datos usaremos la siguiente sintaxis:

```sql
CREATE TABLE new_table AS SELECT * FROM old_table;
```

> Podemos modificar el select para que se guarden cosas en especifico

## Creando una tabla a partir de otra (solo es un clon pero no pasa los datos)

Para crear una tabla a partir de otra sin que se guarden sus datos usaremos la siguiente sintaxis:

```sql
CREATE TABLE new_table LIKE old_table;
```

## Creando llaves primarias y constraints

La sintaxis para crear una llave primaria con constraints a nivel de columna en una tabla en MySQL es la siguiente:

```sql
columna1 TIPO_DATO PRIMARY KEY ATRIBUTOS_DE_COLUMNA ,
```

un ejemplo seria:

```sql
CREATE TABLE `ejemplo`(
    id INT PRIMARY KEY auto_increment,
    nombre VARCHAR(50)
);
```


Si queremos realizar un constraint a nivel de tabla seria:

```sql
[CONSTRAINT [nombreConstraint]] PRIMARY KEY (nombreColumna1 [, nombreColumna2])
```

> Tambien puede ser UNIQUE en lugar de PRIMARY KEY

un ejemplo seria:

```sql
CREATE TABLE `ejemplo`(
    `id` INT auto_increment,
    `nombre` VARCHAR(50),
    CONSTRAINT `ejemplo_pk` PRIMARY KEY (`id`),
    CONSTRAINT `nombre_uq` UNIQUE (`nombre`)
);
```

> *Note* el que nos mas libertad para desarrollar nuestras llaves primarias es la segunda ya que podemos decidir el nombre de nuestra llave primaria.


## Creando llaves foráneas y constraints

La sintaxis para crear una llave foranea en MySQL es la siguiente:

```sql
CONSTRAINT [nombre_constraint] 
FOREIGN KEY [index_name] (col_name[, ...]) 
REFERENCES tbl_name (col_name)
[ON DELETE reference_option {CASCADE | SET NULL | NO ACTION | SET DEFAULT}]
[ON UPDATE reference_option {CASCADE | SET NULL | NO ACTION | SET DEFAULT}]
```

| tipo | funcion |
| - | - |
| CASCADE | significa que cuando se elimina una fila en la tabla de referencia, las filas en la tabla que tienen una llave foránea que se refieren a esa fila también se eliminarán.|
| SET NULL | significa que cuando se elimina una fila en la tabla de referencia o se actualiza la llave foránea a un valor nulo, las filas en la tabla que tienen una llave foránea que se refieren a esa fila se actualizarán a nulo.|
| NO ACTION | significa que no se realizará ninguna acción en las filas de la tabla que tienen una llave foránea que se refieren a la fila eliminada o actualizada en la tabla de referencia.|
| SET DEFAULT | significa que cuando se elimina una fila en la tabla de referencia o se actualiza la llave foránea a un valor nulo, las filas en la tabla que tienen una llave foránea que se refieren a esa fila se actualizarán al valor predeterminado de la columna.|

## Modificando las columnas

Para modificar una tabla en MySQL, se utiliza la sentencia ALTER TABLE. Esta sentencia permite agregar o eliminar columnas, modificar el tipo de datos de una columna, agregar o eliminar índices, entre otras acciones.

* **Ejemplo para agregar una columna:**

```sql
ALTER TABLE nombre_tabla
ADD COLUMN nombre_columna tipo_dato [opciones] [FIRST|AFTER columna_existente];
```

* **Ejemplo para modificar una columna:**

```sql
ALTER TABLE nombre_tabla
MODIFY COLUMN nombre_columna nuevo_tipo_dato [opciones];
```

* **Ejemplo para eliminar una columna:**

```sql
ALTER TABLE nombre_tabla
DROP COLUMN nombre_columna;
```


* **Ejemplo para cambiar el nombre de una columna**

```sql
ALTER TABLE nombre_tabla
CHANGE COLUMN anteriorNombreColumna nuevoNombreColumna tipo_de_dato;
```


## Modificando los constraints y llaves de una tabla

Para modificar los constraints como lo son llaves foraneas o llaves primarias usamos la siguiente sintaxis:

```sql

ALTER TABLE [dbNombre.]nombreTabla
{
    ADD PRIMARY KEY definicionDeConstraint |
    ADD [CONSTRAINT nombreConstraint] FOREIGN KEY definicionDeConstraint |
    DROP PRIMARY KEY |
    DROP FOREIGN KEY nombreConstraint
}
```

> definicionDeConstraint como se realiza en subtema "Creando llaves foráneas y constraints"


## Renombrando, truncando o borrando una tabla

* **Sintaxis para renombrar una tabla**

```sql
RENAME TABLE nombreAntiguo TO nuevoNombre
```

* **Sintaxis para Borrar toda la informacion de una tabla**

```sql
TRUNCATE TABLE nombreTabla;
```

* **Sintaxis para borrar una tabla de la base de datos**

```sql
DROP TABLE nombre;
```
