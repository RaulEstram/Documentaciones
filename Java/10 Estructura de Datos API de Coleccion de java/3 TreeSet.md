# TreeSet 

veamos un codigo de ejemplo de como se utiliza, define y demas de un TreeSet:

```java
package elementos.set;

import modelos.Alumno;

import java.util.*;

public class EjemploTreeSet {

    public static void main(String[] args) {

        // creación de una instancia de un TreeSet
        TreeSet<Integer> ts = new TreeSet<>();
        // otra forma muy util
        Set<Integer> treeSet = new TreeSet<>();

        // agregar elementos, hay que recordad que son ordenados y, por lo tanto, cuando
        // agregamos un nuevo elemento, el Set se ordena y consume recursos

        treeSet.add(5);
        treeSet.add(3);
        treeSet.add(1);
        treeSet.add(4);
        treeSet.add(2);

        System.out.println("treeSet = " + treeSet); // treeSet = [1, 2, 3, 4, 5]

        // Si queremos que el orden sea al revés podemos hacer lo siguiente:
        Set<Integer> setNumeros = new TreeSet<>((a,b) -> b.compareTo(a));
        // lo que estamos haciendo es utilizar funciones lambda donde originalmente es a.compareTo(b)
        setNumeros.addAll(treeSet);
        System.out.println("setNumeros = " + setNumeros);

        // uso de objetos de clases personalizadas

        Set<Alumno> sa = new TreeSet<>();
        sa.add(new Alumno("Raul", 9));
        sa.add(new Alumno("Juan", 8));
        sa.add(new Alumno("Setch", 10));

        System.out.println("sa = " + sa);

    }

}
```

* clase complementaria

```java
package modelos;

public class Alumno implements Comparable<Alumno>{

    private String nombre;
    private Integer nota;

    public Alumno(String nombre, Integer nota) {
        this.nombre = nombre;
        this.nota = nota;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public Integer getNota() {
        return nota;
    }

    public void setNota(Integer nota) {
        this.nota = nota;
    }

    @Override
    public String toString() {
        return "Alumno{" +
                "nombre='" + nombre + '\'' +
                ", nota=" + nota +
                '}';
    }

    @Override
    public int compareTo(Alumno alumno) {
        if (this.nota == null) return 0;
        return alumno.getNota().compareTo(this.nota);
    }

//    @Override
//    public int compareTo(Alumno alumno) {
//        if (this.nombre == null) return 0;
//        return this.nombre.compareTo(alumno.getNombre());
//    }
}
```
