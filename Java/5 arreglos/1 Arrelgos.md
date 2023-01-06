# arreglos 

Los arreglos son tipos de datos de referencia que contienen varios elementos ordenados, una coleccion.

sintaxis:

```java
public class Main {
    public static void main(String[] args) {

        // definir o inicializar un arreglo
        int[] numeros;
        int[] numeros2 = new int[3];
        numeros2[0] = 1;
        numeros2[1] = 2;
        numeros2[2] = 3;
        int[] numeros3 = {1, 2, 3, 4, 5};

        // obtener los valores de un arreglo
        int numero = numeros3[0];

    }
}
```

## Sort

```java
import java.util.Arrays;
import java.util.Collection;
import java.util.Collections;

public class Main {
    public static void main(String[] args) {

        String[] lista = {"hola", "que", "onda", "perros"};
        System.out.println("Arrays.toString(lista) = " + Arrays.toString(lista));
        Arrays.sort(lista);
        System.out.println("Arrays.toString(lista) = " + Arrays.toString(lista));
        Collections.reverse(Arrays.asList(lista));
        System.out.println("Arrays.toString(lista) = " + Arrays.toString(lista));


    }
}
```


## Copiar 2 o mas arrays

Para copiar dos arrays en uno solo en Java, puedes utilizar el método `System.arraycopy()` de la clase **System** de Java. Este método permite copiar una porción de un array en otro array.

Por ejemplo, si quieres copiar dos arrays array1 y array2 en un array result, puedes hacerlo de la siguiente manera:

```java
int[] array1 = {1, 2, 3};
int[] array2 = {4, 5, 6};
int[] result = new int[array1.length + array2.length];

System.arraycopy(array1, 0, result, 0, array1.length);
System.arraycopy(array2, 0, result, array1.length, array2.length);
```

El primer argumento de `arraycopy()` es el array fuente, el segundo es el índice inicial en el array fuente, el tercero es el array destino, el cuarto es el índice inicial en el array destino y el quinto es la cantidad de elementos que se copiarán. En este caso, estamos copiando todos los elementos de ambos arrays.

## Buscar elementos en un arreglo

```java
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        Integer[] list = {1, 2, 3, 4, 5, 19,6,68,3,5};
        List<Integer> lista2 = List.copyOf(Arrays.asList(list));
        System.out.println("index de 68 = "  + lista2.indexOf((Integer) 68));
        System.out.println("lista2.get(7) = " + lista2.get(7));

    }
}
```

## ejemplo de varios metodos de arrays para manejarlos mas facilmente

los metodos que tenemos son:
* sortList para obtener la lista ordenada
* maxElement para obtener el elemento mayor de una lista
* indesOfList para obtener el index de un elemento
* insertInto para insertar un elemento en un index especifico
* deleteElement para eleminar el primer elemento de una lista 

```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] lista = new int[10];

        for (int i = 0; i < 10; i++) {
            lista[i] = i + 1;
        }

        System.out.println("indexOfList(lista, 5) = " + indexOfList(lista, 5));

        separation();

        System.out.println("maxElement(lista) = " + maxElement(lista));

        separation();

        System.out.println("insertInto(lista, 69, 5)");
        System.out.println("Arrays.toString(lista) before = " + Arrays.toString(lista));
        lista = insertInto(lista, 69, 5);
        System.out.println("Arrays.toString(lista) after = " + Arrays.toString(lista));

        separation();

        System.out.println("sortList(lista);");
        sortList(lista);
        System.out.println("Arrays.toString(lista) after = " + Arrays.toString(lista));

        separation();

        System.out.println("deleteElement(lista, 69)");
        lista = deleteElement(lista, 69);
        System.out.println("Arrays.toString(lista) after = " + Arrays.toString(lista));

    }

    public static int indexOfList(int[] list, int value) {
        for (int i = 0; i < list.length; i++) {
            if (list[i] == value) {
                return i;
            }
        }
        return -1;
    }

    public static int maxElement(int[] list) {
        int maxValue = Integer.MIN_VALUE;
        for (int j : list) {
            maxValue = Math.max(maxValue, j);
        }
        return maxValue;
    }

    public static int[] insertInto(int[] lista, int value, int index) {
        int[] result = new int[lista.length + 1];
        System.arraycopy(lista, 0, result, 0, index);
        result[index] = value;
        System.arraycopy(lista, index, result, index + 1, lista.length - index);
        return result;
    }

    public static void sortList(int[] list) {
        Arrays.sort(list);
    }

    public static int[] deleteElement(int[] list, int elemento) {
        int[] result = new int[list.length - 1];
        int indexElement = indexOfList(list, elemento);
        System.arraycopy(list, 0, result, 0, indexElement);
        System.arraycopy(list, indexElement + 1, result, indexElement, result.length - indexElement);
        return result;
    }

    public static void separation(){
        System.out.println("\n\n----------------------------------------------------------\n\n");
    }
}
```