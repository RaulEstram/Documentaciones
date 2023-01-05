# Math - Random

## Obtener un numero aleatorio con Math

```java
public class Main {
    public static void main(String[] args) {

        // Random
        double random = Math.random();
        System.out.println("random = " + random);
    }
}
```

## Obtener un numero aleatorio con Random

Puedes utilizar la clase java.util.Random para generar un número aleatorio entre dos números. Aquí te doy un ejemplo de cómo hacerlo:

```java
import java.util.Random;

public class Main {
  public static void main(String[] args) {
    // Crea un objeto Random
    Random rand = new Random();

    // Genera un número aleatorio entre 0 y 9
    int numeroAleatorio = rand.nextInt(10);
    System.out.println(numeroAleatorio);

    // Genera un número aleatorio entre 5 y 10
    int numeroAleatorio2 = rand.nextInt(6) + 5;
    System.out.println(numeroAleatorio2);
  }
}
```

La clase Random tiene un método llamado nextInt(int n) que genera un entero aleatorio entre 0 (inclusive) y n (exclusive). Por lo tanto, para generar un número aleatorio entre a y b (ambos inclusive), puedes utilizar la siguiente fórmula:

```java
int a = 5;
int b = 10;
int numeroAleatorio = rand.nextInt(b - a + 1) + a;
```