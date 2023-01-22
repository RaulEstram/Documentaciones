# ListIterator 

ListIterator es un tipo de dato que nos permite iterar una lista con un while por ejemplo 

```java
package elementos.set;

import modelos.Alumno;

import java.util.*;

public class EjemploLinkedList {

    public static void main(String[] args) {

        // creacion de una lista con LinkedList
        LinkedList<Alumno> listaALumnos = new LinkedList<>();
        
        // agregar elementos
        listaALumnos.add(new Alumno("Raul", 9));
        listaALumnos.add(0, new Alumno("Setch", 10));
        listaALumnos.addFirst(new Alumno("pepe", 8));
        listaALumnos.addLast(new Alumno("Juan", 8));

        System.out.println("listaALumnos = " + listaALumnos);
        
        ListIterator<Alumno> alumnos = listaALumnos.listIterator();
        
        while (alumnos.hasNext()){
            Alumno alumno = alumnos.next();
            System.out.println("alumno = " + alumno);
        }
        // en este punto el puntero del ListIterator de alumnos está hasta el final por lo que podemos usar el previous
        while (alumnos.hasPrevious()){
            Alumno alumno = alumnos.previous();
            System.out.println("alumno = " + alumno);
        }
    }
}
```