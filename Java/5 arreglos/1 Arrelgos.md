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