# Wrapper

* Cada tipo primitivo tiene su equivalente en un tipo de referencia o clase
* Dan mayor funcionalidad para operaciones de comprobaciones y conversiones

| Tipo primitivo  |  Clase Equivalente  |
| :------------: | :------------: |
| byte  | Byte  |
| short  | Short  |
|  int | Integer  |
| long  |  Long |
| float |  Float |
| double  |  Double |
|  char | Character |
| boolean  | Boolean  |

Los wrapper en pocas palabras son las clases que envuelven a la tipo de dato primitivo, lo que tiene de especial estos wrapper es que podemos utilizar varios metodos y propiedades de estas clases, ya sea para crear instancias, realizar castings, entre otros.

un mini ejemplo seria:

```java
public class Main {
    public static void main(String[] args) {

        // con wrapper
        Integer valor = Integer.valueOf(12345);
        float j = valor.floatValue(); // pasar un wrapper a un primitivo, hay muchos metodos similares
        System.out.println("valor2 = " + valor.toString());

        // sin wrapper/ solo primitivo
        int valor2 = 12345;
        // float j2 = valor2.floatValue(); -> error
        float js = (float) valor2;
        System.out.println("valor2 = " + Integer.toString(valor2));

    }

}
```