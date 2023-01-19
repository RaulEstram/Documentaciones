# Tipos genericos

Los tipos genéricos en Java son una característica que se introdujo en la versión 1.5 de Java para permitir la creación de clases y métodos que funcionan con varios tipos de datos diferentes, en lugar de estar limitados a un tipo específico. Esto permite una mayor flexibilidad y reutilización del código. Los tipos genéricos se especifican mediante el uso de paréntesis angulares < >, dentro de los cuales se especifica el tipo de datos con el que se trabajará. Por ejemplo, una clase genérica para crear una lista se llamaría "List<T>", donde T es el tipo de datos que se utilizará en la lista.

Ejemplo de codigo donde se implementan los tipos de datos genericos:

```java
package generics;

import modelo.Cliente;

import java.util.Arrays;
import java.util.List;

public class EjemploGenericos {
    public static void main(String[] args) {

        Cliente[] clientesArreglo = {new Cliente("nombre1", "apellido1"),
                new Cliente("nombre2", "apellido2"),
                new Cliente("nombre3", "apellido3")};

        Integer[] numerosArreglo = {1, 2, 3};

        List<Cliente> clientesLista = fromArrayToList(clientesArreglo);
        List<Integer> numerosLista = fromArrayToList(numerosArreglo);

        clientesLista.forEach(System.out::println);
        numerosLista.forEach(System.out::println);

        List<Integer> multipleGeneric = fromArrayToListAndPrint(numerosArreglo, clientesArreglo);

    }

    public static <T> List<T> fromArrayToList(T[] clientes) {
        return Arrays.asList(clientes);
    }

    public static <T, I> List<T> fromArrayToListAndPrint(T[] array, I[] arrayToPrint) {

        for (I element : arrayToPrint) {
            System.out.println("element = " + element);
        }

        return Arrays.asList(array);
    }
}
```