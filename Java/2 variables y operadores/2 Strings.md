# Strings

Los strings son una cadena de caracteres que son muy importantes.


## concadenar strings y StringBuilder

Para concadenar Strings tenemos 3 formas para hacerlo y la mas rapida en cualquier caso sera creando un **StringBuilder** por lo cual, seria lo mas recomendado.

```java
public class Main {
    public static void main(String[] args) {
        String nombre = "Raul de Jesus";
        String apellido = "Estrada Zermeño";

        StringBuilder sb = new StringBuilder(nombre);

        for (int j = 0; j < 20; j++) {
            double inicio = System.currentTimeMillis();
            for (int i = 0; i < 10000; i++) {
                // nombre = nombre.concat(" ").concat(apellido).concat("\n"); // mas rapido en pocas iteraciones pero mas lento en muchas que la segunda
                // nombre = nombre + " " + apellido + "\n"; // lento en cortas iteraciones pero mas rapido en muchas iteraciones que la primera forma
                // sb.append(" ").append(apellido).append("\n");// -> el mas rapdio
                continue;
            }
            double fin = System.currentTimeMillis();

            System.out.println(fin-inicio);

        }

    }
}
```


## Metodos relevantes de los Strings

Algunos de los metodos mas utiles que tenemos con los Strings son los siguientes:

```java
public class Main {
    public static void main(String[] args) {
        String nombre = "Raul de Jesus";
        String apellido = "Estrada Zermeño";

        // Returns the length of this string
        System.out.println("apellido.length() = " + apellido.length());
        // Compares this string to the specified object.
        System.out.println("apellido.equals(nombre) = " + apellido.equals(nombre));
        // Compares two strings lexicographically, ignoring case differences
        System.out.println("apellido.compareToIgnoreCase(nombre) = " + apellido.compareToIgnoreCase(nombre));
        // Returns a string that is a substring of this string.
        System.out.println("apellido.substring(0, 7) = " + apellido.substring(0, 7));
        // Returns a string resulting from replacing all occurrences of oldChar in this string with newChar.
        System.out.println("apellido.replace(\"Zermeño\", \"Estrada\") = " + apellido.replace("Zermeño", "Estrada"));
        // Returns the index within this string of the first occurrence of the specified substring.
        System.out.println("apellido.indexOf(\"Estrada\") = " + apellido.indexOf("a"));
        // Returns the index within this string of the last occurrence of the specified character. 
        System.out.println("apellido.indexOf(\"Estrada\") = " + apellido.lastIndexOf("a"));
        // Returns true if and only if this string contains the specified sequence of char values.
        System.out.println("apellido.contains(\"Estrada\") = " + apellido.contains("Estrada"));
        // Tests if this string starts with the specified prefix
        System.out.println("apellido.startsWith(\"Estrada\") = " + apellido.startsWith("Estrada"));
        // Tests if this string ends with the specified suffix.
        System.out.println("apellido.endsWith(\"Estrada\") = " + apellido.endsWith("Zermeño"));
        //Returns a string whose value is this string, with all leading and trailing space removed
        System.out.println("        apellido =                         ".trim() + apellido);

    }

}
```

### Strings to list

```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {

        String file = "cv Estrada Zermeño Raúl de Jesús.pdf";
        
        char[] lista = file.toCharArray();
        System.out.println("file.split(\"\") = " + Arrays.toString(lista));

        String[] lista2 = file.split(" ");
        System.out.println("file.split() = " + Arrays.toString(lista2));

        for (String elemento : lista2) {
            System.out.println("elemento = " + elemento);
        }

    }

}
```