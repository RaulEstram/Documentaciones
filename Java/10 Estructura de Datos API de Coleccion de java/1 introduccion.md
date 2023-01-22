#  API Collections o API de colección de datos.

La API de Collections en Java es un conjunto de clases y interfaces que proporciona una forma de trabajar con colecciones de objetos en Java. La API de Collections se divide en dos partes principales: la interfaz `Collection` y la interfaz `Map`.

La interfaz `Collection` es la interfaz base para todas las colecciones en Java, y proporciona métodos para agregar, eliminar, buscar y recorrer elementos de una colección. Algunas de las clases más comunes que implementan esta interfaz son `ArrayList`, `LinkedList`, `HashSet`, y `TreeSet`.

La interfaz `Map` es una interfaz para almacenar pares clave-valor, y proporciona métodos para agregar, eliminar, buscar y recorrer elementos de una colección. Algunas de las clases más comunes que implementan esta interfaz son `HashMap`, `TreeMap` y `LinkedHashMap`.


> **Note** Aunque tambien hay clases padres que son mucho mas comodas de usar o que se utilizan demasiado tambien como es `List`, `Set` y `Map`, donde `List` almacenará objetos en una secuencia determinada,` Set` no permitiá elementos duplicados y no mantiene el orden de sus elementos y `Map` que almacenan informacón en base a parejas de llaves y valores.

La API de Collections también proporciona varias clases auxiliares, como `Arrays` y `Collections`, que proporcionan métodos estáticos para realizar tareas comunes con colecciones.

En resumen, la API de Collections en Java proporciona un conjunto de clases y interfaces que facilitan el trabajo con colecciones de objetos en Java, permitiendo un fácil manejo de las mismas, agregando, eliminando, buscando y recorriendo los elementos de una colección.

## ¿Qué es una colección?

Una colección es un conjunto de objetos que pueden ser almacenados y accedidos de manera organizada. En el contexto de la programación, las colecciones son utilizadas para agrupar objetos de un mismo tipo y proporcionar una forma de acceder a ellos de manera eficiente.

En Java, la API de Collections proporciona un conjunto de clases y interfaces que permiten trabajar con colecciones de objetos. Estas clases y interfaces proporcionan una forma de almacenar y acceder a los objetos de una manera organizada. Por ejemplo, una clase `ArrayList` almacena objetos en un arreglo, mientras que una clase `HashSet` almacena objetos en un conjunto sin elementos duplicados.

Cada una de estas clases proporciona una funcionalidad específica, como permitir elementos duplicados, mantener el orden de los elementos, proporcionar un acceso rápido a los elementos, entre otras. El uso de colecciones ayuda a organizar y manejar de manera eficiente un gran número de objetos, y es una herramienta fundamental en el desarrollo de aplicaciones en Java.

## Diagrama de clases de la API Collections

[![API Collections diagrama](a "API Collections diagrama")](link_imagen "API Collections diagrama")

### Caracteristicas List

* `ArrayList` es muy bueno para ver datos o acceder a un elemnto en especifico, mientras que `linkedList` no lo es.

* las `linkedList` son buenas para toda la manipulacion de los elementos como eliminarlos y agregar entre medio.

* `ArrayList` es rapido en agregar elemento al final, no entre medio, `LinkedList` es rapido en agregar elemento en cualquier parte

* Las `LinkedList` nos permite implementar pilas y colas.

* `Vector` lo utilizaremos cuando queremos trabajar con hilos.

* Se utiliza el metodo `equals()` para comparar si un elemento es igual a uno que almacena. 

### Caracteristicas Set

* `HashSet` No es ordenado, se agregar elementos con el método `add()` pero no mantiene ningun orden, a pesar de esto es el mas utilizado.

* `TreeSet` Si es ordenado pero no permite duplicados al igual de los demas `Set`

* `HashSet` es mas rapido que el `TreeSet` ya que no tiene que estar ordeando cada vez que se le agrega un nuevo elemento, este segundo se ordena internamente cuando se le agrega un nuevo elemento por lo consume mas recursos.

* TODOS los objetos que almacenemos en un `HashSet` tiene que **implementar** el metodo `hasCode()` para comprar y asegurarse que son elementos unicos.

### Map

* El `HashMap` utiliza el algoritmo `hashCode` por lo que todos los elementos almacenados tienen que implementar este método.

* El `TreeMap` es un mapa ordenado

* las llaves tienen que ser unicas

## Métodos comunes de la API Collections

* `boolean add( Object)` Agrega un elemento a la colección. Devuelve false si no se pudo agregar.

* `boolean addAll( Collection )` Agrega una colección que se pasa por argumento.

* `void clear()` Elimina todos los elementos que componen la colección.

* `boolean contains( Object )` Verdadero si la colección contiene el objeto que se pasa como parámetro, utiliza el método `equals()` para ubicar el objeto.

* `boolean isEmpty()` Verdadero si la colección está vacía, no contiene elementos

* `Iterator iterator()` Devuelve un objeto Iterator que se puede utilizar para avanzar a través de los elementos

* `boolean remove( Object)` Elimina un elemento de la colección y devuelve true si se ha conseguido

* `boolean removeAll ( Collection )` Elimina todos los elementos que están contenidos en el argumento. Devuelve true si consigue eliminar cualquiera de ellos

* `boolean retainAll{ Collection )` Mantiene solamente los elementos que están contenidos en el argumento, es lo que seria una intersección en la teoria de conjuntos. Devuelve verdadero en caso de que se produzca algún cambio

* `int size()` Devuelve el número de elementos que componen la colección

* `Object[] toArrav` nos regresa un array.