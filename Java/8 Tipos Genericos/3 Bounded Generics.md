# Bounded Generics

Los Bounded Generics en Java son una extensión de los tipos genéricos que permiten especificar un rango o límite de tipos de datos que se pueden utilizar con una clase o método genérico.

## Metodos con Bounded Generics

Para especificar el tipo de Bounded Generics en un metodo tenemos que usar la palabra **extends** al especificar que es un metodo con tipo de datos genericos, al igual que tenemos que especificar el tipo de dato de acepta.

Podemos tener varios metodos con el mismo nombre, pero que aceptan diferentes tipos de datos, y se utilizara el metodo con el que tenga mejor compatibilidad un tipo de dato.


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
        clientesLista.forEach(System.out::println);
        
        List<Integer> numerosLista = fromArrayToList(numerosArreglo);
        numerosLista.forEach(System.out::println);

    }
    public static <T> List<T> fromArrayToList(T[] clientes) {
        return Arrays.asList(clientes);
    }

    public static <T extends Number> List<T> fromArrayToList(T[] clientes) {
        System.out.println("Number");
        return Arrays.asList(clientes);
    }

}
```

Tambien podemos especififcar si queremos que implemente una interfaz por ejemplo:

En el siguiente ejemplo especificamos que solamente podemos utilizar datos de tipo Cliente y que implementen Comparator, por ejemplo si tuvieramos una clase ClientePro que hereda de Cliente y que implemente Comparator, podria utilizar este metodo, gracias al polimorfismo y que implementa la interfaz

```java
    public static <T extends Cliente & Comparator<T> > List<T> fromArrayToList(T[] clientes) {
        System.out.println("Number");
        return Arrays.asList(clientes);
    }
```
