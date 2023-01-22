# LinkedList

LinkedList es otro tipo de lista que agrega mas metodos para agregar o eliminar elementos de la lista, es por esto que si queremos usarlos no debemos usar el polimorfismo y debemos definirlo con LinkedList en lugar de simplemente List.

veamos un ejemplo con algunos métodos que tiene este tipo de lista


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
        
        // obtener elementos con exception
        System.out.println("listaALumnos.getFirst() = " + listaALumnos.getFirst());
        System.out.println("listaALumnos.getLast() = " + listaALumnos.getLast());
        System.out.println("listaALumnos.get(1) = " + listaALumnos.get(1));

        System.out.println("listaALumnos = " + listaALumnos);
        // obtener elementos sin exception pero si con null
        System.out.println("listaALumnos.peekFirst() = " + listaALumnos.peekFirst());
        System.out.println("listaALumnos.peekLast() = " + listaALumnos.peekLast());
        System.out.println("listaALumnos.peek() = " + listaALumnos.peek());

        System.out.println("listaALumnos = " + listaALumnos);

        // eliminar elementos con exception
        System.out.println("listaALumnos.removeFirst() = " + listaALumnos.removeFirst());
        System.out.println("listaALumnos.removeLast() = " + listaALumnos.removeLast());

        System.out.println("listaALumnos = " + listaALumnos);

        // "eliminar" elementos sin exception pero si con null
        System.out.println("listaALumnos.pollFirst() = " + listaALumnos.pollFirst());

        // eliminar elemento final siempre
        System.out.println("listaALumnos.pop() = " + listaALumnos.pop());

        System.out.println("listaALumnos = " + listaALumnos);
    }
}
```