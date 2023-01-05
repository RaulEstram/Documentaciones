# Autoboxing y unboxing

El autoboxing y el unboxing son dos características de Java que permiten la conversión automática entre tipos primitivos y sus correspondientes tipos de envoltorio (wrapper types) en Java. El autoboxing es la conversión automática de un tipo primitivo a su tipo de envoltorio correspondiente, mientras que el unboxing es la conversión automática de un tipo de envoltorio a su tipo primitivo correspondiente.

Por ejemplo, el siguiente código muestra el autoboxing y el unboxing en acción:

```java
// Autoboxing
Integer x = 10; // aquí, el int 10 se convierte automáticamente a un Integer

// Unboxing
int y = x; // aquí, el Integer x se convierte automáticamente a un int
```

Otro ejemplo seria el siguiente:

```java
public class Main {
    public static void main(String[] args) {

        Integer num1 = Integer.valueOf(1000);
        Integer num2 = 1000; // se realiza automanticamente el autoboxing
        Integer num3 = num1;

        System.out.println(num1 == num2); // false porque tienen referencias de objetos diferentes
        System.out.println(num1 == num3); // true porque tienen referencias de objetos iguales
        System.out.println(num1.equals(num2)); // true porque ahora usa un método para comprar el valor y no el objeto
        System.out.println(num1.intValue() == num2.intValue()); // true porque se usa intValue y ahora se comparan primitivos y no wrappers
        System.out.println(num1 > num2); // false, porque se realiza automáticamente un unboxing, esto pasa con los <>

    }

}

```

> para comprar wrappers generalmente usamos el equals, pero cuando hablamos de booleans, no lo usamos, usamos simplemente "=="