# clase Date

Para las fechas podremos utilizar principalmente las clases **Date, SimpleDateFormat** y metodos como **getTime()** de la clase **Date**.

En pocas palabras:

* **Date** nos servira para definir u obtener la fecha
* **SimpleDateFormat** nos sirve para pasar un Date a un String o viceversa

Un ejemplo seria el siguiente:

```java
import java.text.SimpleDateFormat;
import java.util.Date;

public class Main {
    public static void main(String[] args) {

        Date fecha = new Date();
        System.out.println("fecha = " + fecha);

        SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MMMM/yyyy");
        String fechaStr = dateFormat.format(fecha);
        System.out.println("fechaStr = " + fechaStr);

    }

}
```

## Definir fechas

Un ejemplo de como podemos definir fechas futuras o pasadas con Date es el siguiente ejemplo:

```java
import java.text.SimpleDateFormat;
import java.util.Calendar;
import java.util.Date;

public class Main {
    public static void main(String[] args) {
        // Definimos un calendar o en otras palabras una fecha personalizada
        Calendar calendar = Calendar.getInstance();
        // calendar.set(2023, Calendar.FEBRUARY, 13, 13, 13 , 13);
        calendar.set(Calendar.YEAR, 2023);
        calendar.set(Calendar.DAY_OF_MONTH, 13);
        calendar.set(Calendar.MONTH, Calendar.FEBRUARY);
//        calendar.set(Calendar.HOUR_OF_DAY, 13);
        calendar.set(Calendar.HOUR, 11);
        calendar.set(Calendar.AM_PM, Calendar.AM);
        calendar.set(Calendar.MINUTE, 13);
        calendar.set(Calendar.SECOND, 13);

        // obtenemos el Date de nuestro Calendar para poder utilizar SimpleDateFormat o para usarlo como Date
        Date dateCalendar = calendar.getTime();

        // Creamos nuestro Date con el tiempo actual
        Date fecha = new Date();

        // creamos nuestro SimpleDateFormat para imprimir bonito los Date
        SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MMMM/yyyy; HH:mm:ss; z");

        // imprimimos nuestros Date
        System.out.println("dateFormat.format(fecha) = " + dateFormat.format(fecha));
        System.out.println("dateFormat.format(dateCalendar) = " + dateFormat.format(dateCalendar));
    }

}
```

## Comparar fechas

Podemos usar los metodos **before, after o compareTo** de la clase Date para comparar 2 fechas.

```java
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

        SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
        Scanner scanner = new Scanner(System.in);
        System.out.println("Digite una fecha en el formato dd/mm/yyyy: ");
        String fechaStr = scanner.nextLine();

        try {
            Date fechaIngresada = dateFormat.parse(fechaStr);
            Date fechaActual = new Date();

            System.out.println("dateFormat.format(fechaIngresada) = " + dateFormat.format(fechaIngresada));
            System.out.println("dateFormat.format(fechaActual) = " + dateFormat.format(fechaActual));

            // COMPARAR FECHAS 1
            // fechaIngresada > fechaActual == true
            if (fechaIngresada.after(fechaActual)) {
                System.out.println("La fecha ingresada por el usuario es posterior a la fecha actual");
            } else if (fechaIngresada.before(fechaActual)) {
                System.out.println("La fecha ingresada por el usuario es anterior a la fecha actual");
            } else {
                System.out.println("Las fechas son exactamente iguales");
            }
            
            // COMPARAR FECHAS 2
            if (fechaIngresada.compareTo(fechaActual) > 0) {
                System.out.println("La fecha ingresada por el usuario es posterior a la fecha actual");
            } else if (fechaIngresada.compareTo(fechaActual) < 0) {
                System.out.println("La fecha ingresada por el usuario es anterior a la fecha actual");
            } else if (fechaIngresada.compareTo(fechaActual) == 0) {
                System.out.println("Las fechas son exactamente iguales");
            }


        } catch (ParseException e) {
            System.out.println("Error en el formato de la fecha");
        }

    }

}
```

## ejemplo obtener edad:

```java
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

        // creación del SimpleDateFormat para el casting de String a Date
        SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
        // creación de una instancia de Scanner para pedir al usuario su fecha de nacimiento
        Scanner scanner = new Scanner(System.in);
        // Obtenemos la fecha actual
        Date fechaActual = new Date();
        
        // pedimos al usuario su fecha de nacimiento y la almacenamos en un String
        System.out.print("Digite su fecha de nacimiento con el formato dd/MM/yyyy: ");
        String fechaNacimientoStr = scanner.nextLine();
        
        // uso de try para el error ParseException
        try {
            // Obtenemos un Date mediante el String de la fecha de nacimiento
            Date fechaNacimiento = dateFormat.parse(fechaNacimientoStr);
            // Calculamos la fecha
            short edad = (short) ((fechaActual.getTime() - fechaNacimiento.getTime()) / (1000L * 60 * 60 * 24 * 365));
            // imprimimos la fecha
            System.out.println("edad = " + edad);
        } catch (ParseException e) {
            System.out.println("Se produjo un error :c");
        }

    }

}
```


> [documentacion de SimpleDateTime](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/text/SimpleDateFormat.html)