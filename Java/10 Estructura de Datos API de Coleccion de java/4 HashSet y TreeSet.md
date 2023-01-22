# Diferencias entre HashSet y TreeSet

las diferencias internas entre un hashSet y TreeSet en cuanto a su funcionamiento al implementar clases nuestras son las siguientes:

* Un TreeSet solamente necesita el metodo `compareTo()` ya que si este regresa 0 sabe que 2 elementos son iguales y por lo tanto no lo agrega al Set, esto teniendo en cuenta contra que datos los estas comparando.

* Un HashSet como no ordena no ocupa el `compareTo()` por lo que en su lugar necesita el método `equals()` y `hashCode()` en los objetos que va almacenar