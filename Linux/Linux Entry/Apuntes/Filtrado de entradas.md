# Filtrado de entradas

El comando **grep** es un filtro de texto que busca líneas en una entrada y devolverá aquellas que coincidan con un patrón determinado.

```terminal
$ grep [OPCIONES] PATRÓN [ARCHIVO]
```

este comando nos puede funcionar si tenemos archivos muy grandes y queremos obtener alguna pieza de informacion en especial, por ejemplo en un archivo sql podemos buscar piezas de informacion de algun id en contreto.
Ejemplo:

```$ grep 10001 backup.sql```

> **Note**
> grep es capaz de interpretar patrones de búsqueda mucho más complejos.
