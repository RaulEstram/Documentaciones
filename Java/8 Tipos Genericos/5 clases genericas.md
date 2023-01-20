# clases genericas

Para definir que una clase es generica tenemos que agregar `<T>` despues del nombre de la clase, para que posteriormente podamos utilizar `T` en metodos, porpiedades y demas para decir que se le puede pasar cualquier tipo de Objeto.

En el siguiente ejemplo podemos apreciar como tenemos una clase generica en donde le pasamos `T` como parametro que nos dice que puede ser cualquier tipo de dato, y tambien se le agrega a la interfaz `Iterable` ya que esta clase tambien es Generica o lo permite.

Tambien podemos ver en el main como es que tenemos que instanciar una clase de tipo generica usando `<>`.


* clase generica

```java
package genericsclass;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class Camion<T> implements Iterable<T> {

    private final List<T> objetos;
    private int maxObjects;

    public Camion(int maxObjects) {
        this.objetos = new ArrayList<>();
        this.maxObjects = maxObjects;
    }

    public void add(T object) {
        if (this.objetos.size() >= maxObjects) throw new RuntimeException("No hay mas espacio");
        this.objetos.add(object);
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

    public List<T> getObjetos() {
        return objetos;
    }

    public int getMaxObjects() {
        return maxObjects;
    }

    public void setMaxObjects(int maxObjects) {
        this.maxObjects = maxObjects;
    }
}
```

* Main

```java
import genericsclass.Auto;
import genericsclass.Camion;

public class Main {
    // java - unused declaration
    public static void main(String[] args) {

        Camion<Auto> camion = new Camion<>(3);

        camion.add(new Auto("vocho"));
        camion.add(new Auto("mamalona"));
        camion.add(new Auto("vmw"));

        camion.forEach(System.out::println);

        for (Auto o : camion) {
            System.out.println(o);
        }
    }

}
```