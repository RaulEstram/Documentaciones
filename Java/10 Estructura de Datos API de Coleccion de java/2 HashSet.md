# HashSet 

Los HashSet en Java son una implementación de un conjunto de datos que utilizan una estructura de datos llamada tabla hash para almacenar elementos. Los conjuntos no permiten elementos duplicados y no garantizan un orden específico para los elementos. Los HashSet son útiles para almacenar conjuntos de elementos y realizar operaciones de conjunto, como la unión, intersección y diferencia. También son útiles para verificar si un elemento se encuentra o no en el conjunto en tiempo constante mediante el uso de la función hash.

veamos un codigo de ejemplo de como se utiliza, define y demas de un HashSet

```java
package elementos.set;

import java.util.*;

public class EjemploHashSet {

    public static void main(String[] args) {

        // definimos un HashSet
        HashSet<String> hs = new HashSet<>();
        // también podemos definirlo de la forma más generica cuando se utilizara cosas básicas
        Set<String> hashSet = new HashSet<>();

        // agregar elementos a un HashSet
        hashSet.add("Uno");
        hashSet.add("Dos");
        hashSet.add("Tres");
        hashSet.add("Cuatro");
        
        // imprimir un HashSet
        System.out.println("hashSet = " + hashSet);

        // No permite duplicados
        System.out.println("hashSet.add(\"Dos\") = " + hashSet.add("Dos")); // false

        // Podemos crear un List a partir de un Set y viceversa
        // set a list
        List<String> listaNumeros = new ArrayList<>(hashSet);
        System.out.println("listaNumeros = " + listaNumeros);

        // list a set
        Set<String> setNumeros = new HashSet<>(listaNumeros);
        System.out.println("setNumeros = " + setNumeros);

        // detectando duplicados
        String[] cosas = {"Helado", "Rocas", "Peluches", "Ordenadores", "Comida", "Peluches", "Ordenadores"};

        Set<String> unicos = new HashSet<>();
        
        for(String elemento: cosas){
            if (!unicos.add(elemento)){
                System.out.println("Elemento duplicado: " + elemento);
            }
        }

        System.out.println(unicos.size() + " elementos no duplicados: " + unicos);


    }
}
```