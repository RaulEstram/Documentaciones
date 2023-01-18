# Interfaz

En Java, una interfaz es una especificación de un conjunto de métodos que pueden ser implementados por una clase. Una interfaz no tiene código implementado, solo define los métodos y sus firmas. Las clases que implementan una interfaz deben proporcionar código para todos los métodos definidos en la interfaz. Las interfaces también pueden contener constantes. Una clase puede implementar varias interfaces.


> **Note** Las interfaces permiten la herencia multiple, o mejor dicho que una clase puede implementar varias interfaces

## utilidades

Las interfaces en Java sirven para varios propósitos:

* Permiten la abstracción de un conjunto de métodos y constantes, lo que permite a las clases implementar ese conjunto de métodos y constantes de manera consistente.

* Permiten la herencia múltiple de comportamiento, ya que una clase puede implementar varias interfaces.

* Ayudan a establecer contratos entre clases, ya que las clases que implementan una interfaz deben proporcionar implementaciones para todos los métodos definidos en la interfaz.

* Ayudan a la polimorfismo ya que las clases que implementan una interfaz pueden ser tratadas como instancias de esa interfaz.

* Permiten la creación de bibliotecas de clases genéricas que pueden ser utilizadas por varios programas.

## Diseño orientado a las interfaces

* En Java, las interfaces permiten pasar del estilo de diseño **"orientado a la implementación"** a uno **"orientado a la interfaz"**
* Donde todas las clases acceden a servicios a través de interfaces que son implementadas por clases concretas
* Y al no depender de clases concretas (solo de entidades abstractas) nuestro diseño será más reutilizable

## Sintaxis 

la sintaxis de las interfaces es la siguiente:


*  interface

```java
public interface Imprimible{
    public void imprimir();
}
```

* clase que implementa la interfaz

```java
public class Libro implements Imprimible{
    @override
    public void imprimir(){
        // imprimiendo libro
    }
}
```

## default y static en interfaces

en las interfaces tambien se le pude dar funcionamentos en sus metodos por defecto en java 8 como es el siguiente ejemplo:

* default

```java
package poointerfaces.interfaces;

public class EjemploInterfaz {

    default void imprimir(){
        System.out.println("hola");
    }

}
```

* static

```java
package poointerfaces.interfaces;

public class EjemploInterfaz {

    final static String TEXTO = "hola";

    static String imprimir(String texto){
        return texto;
    }

}
```