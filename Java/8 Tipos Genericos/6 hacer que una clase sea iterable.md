# hacer que una clase sea iterable

Para que una clase sea iterable tenemos que implementar la interfaz `Iterable` donde tendremos que implementar el método `iterator`.

Una forma para implementar esto es si la clase tiene un List el cual podemos regresar como un Iterator.

Un ejemplo es el siguiente:

```java
package genericsclass;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class Camion implements Iterable{

    private List objetos;
    private int maxObjects;

    public Camion(int maxObjects) {
        this.objetos = new ArrayList();
        this.maxObjects = maxObjects;
    }

    public Camion add(Object object){
        if (this.objetos.size() >= maxObjects) throw new RuntimeException("No hay mas espacio");

        this.objetos.add(object);

        return this;
    }

    @Override
    public Iterator iterator() {
        return this.objetos.iterator();
    }

    @Override
    public String toString() {
        return "Camion{" +
                "objetos=" + objetos +
                ", maxObjects=" + maxObjects +
                '}';
    }
}
```

* main

```java
import genericsclass.Auto;
import genericsclass.Camion;

public class Main {
    // java - unused declaration
    public static void main(String[] args) {

        Camion camion = new Camion(3);

        camion.add(new Auto("vocho"))
                .add(new Auto("mamalona"))
                .add(new Auto("vmw"));

        camion.forEach(System.out::println);

        for (Object o: camion){
            System.out.println(o);
        }
    }

}
```