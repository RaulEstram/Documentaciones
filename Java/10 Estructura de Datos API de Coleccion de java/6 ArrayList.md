# ArrayList

veamos un ejemplo de ArrayList

```java
package elementos.set;

import modelos.Alumno;

import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

public class EjemploArrayList {

    public static void main(String[] args) {

        // creacion de una lista con ArrayList
        List<Alumno> listaALumnos = new ArrayList<>();
        listaALumnos.add(new Alumno("Raul", 9));
        listaALumnos.add(new Alumno("Juan", 8));
        listaALumnos.add(new Alumno("Juan", 8));
        listaALumnos.add(new Alumno("Setch", 10));

        // 3 formas de ordenar una lista
        // utiliza el metodo compareTo dentro de la clase
        Collections.sort(listaALumnos);
        // le pasamos una lambda para realizar el compareTo desde aquí.
        listaALumnos.sort((alumno1, alumno2) -> alumno1.getNombre().compareTo(alumno2.getNombre()));
        // Utilizando la clase Comparator y el método comparing
        listaALumnos.sort(Comparator.comparing(Alumno::getNota).reversed());

        System.out.println("listaALumnos = " + listaALumnos);
        
        // agregar en otra parte que no sea el final
        listaALumnos.add(1, new Alumno("Raúl", 10));

        System.out.println("listaALumnos = " + listaALumnos);

        // eliminar un elemento por instancia, utiliza el equals() del objeto Alumno
        listaALumnos.remove( new Alumno("Raúl", 10));

        // eliminar un elemento por índice, utiliza el equals() del objeto Alumno
        listaALumnos.remove(0);
    }
}
```

## Métodos importantes de los ArrayList

Dentro de los metodos importantes podemos verlos en el **10.1 introduccion** en la seccion de metodos importantes, algunos de estos metodos utilizaran los metodos de nuestra clase como son `equals()` o `compareTo` hay que tener en cuenta eso.