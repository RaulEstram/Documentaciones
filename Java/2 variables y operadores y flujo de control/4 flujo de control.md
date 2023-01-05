# Sentencias de control

las sentencias de control son una clave fundamental en la programacion y tenemos varias sentencias.

## if - else if - else

se pueden agregar los else if que se quiera.

```java
public class Main {
    public static void main(String[] args) {

        int option = 1;

        if (option == 1) {
            // bloque a ejecutar si cumple la condicion
        } else if (option == 2) {
            // bloque a ejecutar si cumple la segunda condicion pero no la primera
        } else {
            // bloque a ejecutar si no cumple con ninguna condicion
        }

    }

}
```

## switch case

Es importante no olvidar los **break** porque si no ejecutara el siguiente case.

```java
public class Main {
    public static void main(String[] args) {

        int option = 1;

        switch (option) {
            case 1:
                // ejecuta sentencia 1
                System.out.println("option es 1= " + option);
                break;
            case 2:
                // ejecuta sentencia 2
                System.out.println("option es 2= " + option);
                break;
            default:
                // si no existe coincidencia, se ejecuta la sentencia default

        }

    }

}
```

## while 

se ejecuta su bloque de codigo si y solo si el condicion evaluda es verdadera

```java
public class Main {
    public static void main(String[] args) {

        int numero = 1;

        while (numero < 11){
            numero++;
        }

    }

}
```

## do - while

se ejecuta por lo menos unas vez su bloque de codigo, porteriormente evalua su condicion y si esta es verdadera, ejecutara el bloque de codigo otra vez.

```java
public class Main {
    public static void main(String[] args) {

        int numero = 1;

        do{
            System.out.println("numero = " + numero);
            numero++;
        }while (numero < 11);

    }

}
```

## for 

```java
public class Main {
    public static void main(String[] args) {

        for (int i = 0; i < 11; i++) {
            System.out.println("i = " + i);
        }
        
    }

}
```

## for each

sirve para iterar los elementos como tal de un iterable como una lista:

```java
public class Main {
    public static void main(String[] args) {

        int[] lista = {1, 2, 3, 4, 5, 6, 7, 8, 9};

        for (int elemento : lista) {
            System.out.println("elemento = " + elemento);
        }

    }

}
```

## etiquetas en sentencias

las etiquetas se pueden usar en los for y en los while.

y se usan en conjunto con los continue o los brake

```jova
public class Main {
    public static void main(String[] args) {
        foruno:
        for (int i = 0; i < 11; i++) {
            fordos:
            for (int j = 0; j < 11; j++) {
                fortres:
                for (int k = 0; k < 10; k++) {
                    if (k >= 8) {
                        continue foruno;
                    }
                    if (j >= 5) {
                        break fordos;
                    }
                    System.out.println("(" + i + ", " + j + ", " + k + ")");
                }
            }
        }

    }

}
```

### ejemplo buscar cantidad de palabras en una frase

```java
public class Main {
    public static void main(String[] args) {


        String frase = "trigo tres tristes tigres tragan trigotrigo en un trigaltrigotrigo";
        String palabra = "trigo";
        int cantidad = 0;

        // iterar toda la frase
        iterarFrase:
        for (int i = 0; i < frase.length(); i++) {
            int aux = i;

            // comprobar si las palabras siguientes corresponden con la palabra
            for (int j = 0; j < palabra.length(); j++) {
                if (frase.charAt(aux++) != palabra.charAt(j)) {
                    continue iterarFrase;
                }
            }

            // incrementar en 1 la cantidad
            cantidad++;
        }

        System.out.println("cantidad = " + cantidad);


    }

}
```