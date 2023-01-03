# Introduccion a las vairables

Una declaración de vairable siempre contiene dos partes, el tipo de dato de la variable y su nombre, por ejemplo: `TipoDato nombreVariable;`.

El tipo de la variable determina los valores que la variable puede contener y las operaciones que se pueden realizar con ella.

---

### Categorías de tipos

existen 2 categorías de datos principales.

1. primitivos
2. referencia

Los tipos primitivos contienen un sólo valor e incluten los tipos como los enteros, flotantes, los caracteles, booleanos, etc.

como tipos de datos refernciados tenemos los arreglos, las clases y las interfaces.

Ejemplo de datos de tipo primitivos:

```java
public class Main {
    public static void main(String[] args) {

        // Primitivos

        // BOOLEAN
        boolean a = true;
        boolean b = false;

        // CHAR
        // Usa el código UNICODE y ocupa cada carácter 16 bits
        char character1 = 'a';
        char character2 = '\u0021'; // !

        // ENTEROS
        // -128 a 127
        byte enteroByte = 127;
        // entre -32768 a 32767
        short enteroShort = 32_767;
        // entre -2147483648 a 2147483647
        int enteroInt = 2_147_483_647;
        // entre -9223372036854775808 a 9223372036854775807
        long enteroLong = 9_223_372_036_854_775_807L;

        // FLOTANTES
        // entre -1.4E-45 a 3.4028235E38
        float realFloat = 3.1416f;
        // entre -4.9E-324 a 1.7976931348623157E308
        double realDouble = 4.702_923_5E3;

        // DINÁMICO
        var dynamic = 31.5;

    }
}
```

## Entras de los tipos de datos primitivos

* se pueden hacer conversiones entre estos tipos de datos usando
    * String to data -> usando la clase del tipo de datos con su metodo parse
    * haciendo casting `(tipo de dato para hacer el casting) value`
    * data to String -> usando la clase String con su metodo valueOf

