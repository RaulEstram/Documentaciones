# varargs

estos metodos o funciones con varargs con funciones que se le pasa un tipo especial de parametro para que pueda aceptar varios elementos de un solo tipo y que los almacena en un arreglo.

veamos un ejemplo:

```java

public class Main {

    public static void main(String[] args) {

        System.out.println(sumar(1, 2, 3, 4, 5, 6, 7, 8, 9, 10));

    }

    public static int sumar(int... numeros) {
        int total = 0;
        for (int numero : numeros) {
            total += numero;
        }
        return total;
    }
}

```