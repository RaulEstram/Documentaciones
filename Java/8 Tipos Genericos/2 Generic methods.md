# Generic Methods

Los métodos genéricos en Java son métodos que pueden trabajar con varios tipos de datos diferentes. 

Para especificar que un metodo es de tipo generito tenemos que poner **"<T>"** despues de los modificadores de acceso y antes del tipo de dato que regresa el método, en donde T puede ser caulquier letra que sea, por convencion se usa la T.

Se puede definir que se utilizan varios de estos tipos como se puede apreciar en el siguiente ejemplo:

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