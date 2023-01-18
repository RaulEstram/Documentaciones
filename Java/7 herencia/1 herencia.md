# Herencia

La herencia en Java es un mecanismo por el cual una clase puede heredar los atributos y métodos de otra clase. La clase heredera se llama subclase o clase hija, mientras que la clase de la cual se hereda se llama superclase o clase padre. La herencia permite la reutilización de código y la organización jerárquica de las clases en un programa.

Para implementar la herencia utilizamos la palabra **extends** por ejemplo:

```java
class Persona{...}
class Profesor extends Persona{...}
class Alumno extends Persona{...}
class AlumnoInternacional extends Alumno{...}
```

> En java no hay herencia multiple


## Polimorfismo 

El polimorfismo en Java es un mecanismo que permite que una variable de una clase padre pueda hacer referencia a un objeto de una clase hija. Es decir, una variable de una clase padre puede almacenar un objeto de una clase hija que hereda de esa clase padre. Esto permite tratar objetos de diferentes clases de manera similar y escribir código más genérico.

El polimorfismo también permite que un método de una clase padre pueda ser sobreescrito (overriden) por un método de una clase hija y ser comportarse de manera diferente dependiendo del objeto al que se aplique.
En resumen, el polimorfismo permite escribir código que puede trabajar con objetos de diferentes tipos, pero que tienen algo en común, y pueden comportarse de manera diferente dependiendo del objeto con el que se esté trabajando.

> Cuando definimos o asignamos una instancia de clase hija a una de clase padre (`Persona alumno = new Alumno();`) no podremos utilizar metodos de la clase hija, solamente de la clase padre. Si queremos utilizar los metodos de la clase hija tenemos que realizar un casting "`((Alumno)alumno).setInstitucion("instituto");`"

## Generalizacion y especializacion

La generalización y especialización en Java se refieren a los conceptos de herencia y polimorfismo.
La generalización se refiere a la relación entre una clase padre y una clase hija, donde la clase hija hereda los atributos y métodos de la clase padre. La clase padre se considera una generalización de la clase hija, ya que es más genérica y contiene características comunes a varias clases específicas.

La especialización se refiere a la relación inversa, donde una clase hija se considera una especialización de una clase padre, ya que tiene características específicas que la diferencian de otras clases hijas.
En resumen, la generalización es un mecanismo para crear una jerarquía de clases donde una clase padre es una generalización de varias clases hijas y la especialización es un mecanismo para crear clases hijas que tienen características específicas que las diferencian de otras clases hijas.

## Super

La palabra reservada "super" en Java se utiliza para hacer referencia a la clase padre de la clase actual. Se utiliza principalmente en dos casos:

* Acceso a los atributos y métodos de la clase padre: Cuando una clase hija desea acceder a los atributos o métodos de su clase padre, puede utilizar la palabra clave "super" para hacerlo. Por ejemplo, si una clase hija desea llamar a un método de su clase padre, puede hacerlo utilizando "`super.nombreDelMetodo()`".

* Llamar al constructor de la clase padre: Cuando una clase hija desea llamar al constructor de su clase padre, puede utilizar la palabra clave "super" seguida de los argumentos necesarios para llamar al constructor deseado. Por ejemplo, "`super(argumentos);`".

En resumen "super" en java, se utiliza para acceder a los atributos y métodos de la clase padre y para llamar al constructor de la clase padre.

## Impedir la herencia

para impedir la herencia en java es necesario utilizar la palabra `final` en donde se define la clase:

`final public class Persona {...}`

## Protected y privated en herencia

Cuando se trata de herencia en Java, es recomendable usar "protected" para los atributos y métodos en lugar de "private".

La razón principal es que "private" restringe el acceso a los atributos y métodos solo a la clase que los define, mientras que "protected" permite el acceso a esos mismos atributos y métodos desde cualquier clase que herede de la clase original.

Usando "private" en atributos y métodos, limita la capacidad de la clase hija para acceder y modificar estos, lo que dificulta la reutilización de código y hace que sea más difícil para la clase hija para sobrescribir o extender la funcionalidad de la clase padre.

En resumen, usar "protected" en lugar de "private" permite una mayor flexibilidad y reutilización de código en una jerarquía de herencia. Sin embargo, es importante también tener en cuenta los principios de encapsulamiento y evitar exponer detalles de implementación innecesarios a las clases hijas.

> el protected funciona de la anterior forma siempre y cuando esten en el mismo paquete

