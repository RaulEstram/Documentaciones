# Ejemplo full

En este ejemplo veremos el codigo de un ejemplo que implementa cosas como:

* clases abstract
* Interfaces
* tipos genericos
* POJO (Plain Old Java Object) u Objeto Plano (Simple) de java, el cual nos ayuda a que interfaces o clases puedan utilizar caracteristicas o metodos en espacial a pesar de que se implementa tipos genericos.


Se vera un ejemplo donde se crearan clases que simulen que dentro de estas tienen una base de datos mediante un `List` y que tendran varios metodos basicos de un CRUD.

Para esto tendran que implementar varias interfaces con tipos de datos genericos en especificos y para la realizacion de algunos de estos metodos tendran que usar estos objetos especificos que hereden de un POJO para el control de IDs.



## POJO o Plain Old Java Object

POJO es un acrónimo en inglés que significa "Plain Old Java Object". Es un término utilizado para describir objetos de Java simples que no tienen ninguna dependencia o relación con una tecnología o framework específico. Un POJO es simplemente una clase Java que tiene propiedades (atributos) y métodos (funciones) como cualquier otra clase, pero no tiene ninguna anotación ni implementación especial. Estos objetos son fáciles de entender y utilizar, y son ampliamente utilizados en la programación orientada a objetos.

Por lo tanto crearemos un POJO que tenga una implementacion basica de ID para que nuestras interfaces puedan utilizar el metodo `getId()` de las clases que hereden de este POJO y se facilite las implementaciones de metodos de tipo CRUD que se necesiten los id de los objetos.

* clase POJO

```java
package modelo;

public class BaseEntity {

    protected final Integer id;
    private static int ultimoId;

    public BaseEntity() {
        this.id = ++ultimoId;
    }

    public Integer getId() {
        return id;
    }
}
```

### Implementacion del POJO

para implementar este POJO tenemos que hacer que una clase herede de esta, y estas clases seran las que posteriormente se podran utilizar como tipos de datos, en clases que implementen todas las interfaces para el manejo del crud.

```java
package modelo;

import java.util.Objects;

public class Cliente extends BaseEntity {

    // PROPRIETIES
    private String nombre, apellido;


    public Cliente(String nombre, String apellido) {
        super();
        this.nombre = nombre;
        this.apellido = apellido;
    }

    // METHODS

    @Override
    public String toString() {
        return "Cliente[" +
                "id = " + id +
                ", nombre = '" + nombre + '\'' +
                ", apellido = '" + apellido + '\'' +
                ']';
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Cliente cliente = (Cliente) o;
        return Objects.equals(id, cliente.id);
    }


    // GETTERS & SETTERS

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public String getApellido() {
        return apellido;
    }

    public void setApellido(String apellido) {
        this.apellido = apellido;
    }
}
```

## Creacion de interfaces con tipos de datos genericos en especifico

Las siguiente interfaces son las que tienen los metodos que tienen que implementar las clases que simulen el CRUD.

* CrudRespositorio

```Java
package repositorio;

import java.util.List;

public interface CrudRepositorio<T> {

    List<T> listar();

    T buscarPorId(Integer id);

    void crear(T t);

    void editar(T t);

    void eliminar(Integer id);

}
```

* OrdenableRespositorio

```Java
package repositorio;

import java.util.List;

public interface OrdenableRepositorio<T> {

    List<T> listar(String campo, Direccion direccion);

}
```

para este se necesita el enum siguiente:

```java
package repositorio;

public enum Direccion {
    ASC("Ascendente"),
    DESC("Descendente");

    final String direccion;

    Direccion(String direccion) {
        this.direccion = direccion;
    }

    public String getDireccion() {
        return direccion;
    }
}
```


* PaginableRespositorio

```Java
package repositorio;

import java.util.List;

public interface PaginableRepositorio<T> {

    List<T> listar(int desde, int hasta);

}
```

* OrdenablePaginableCrudRepositorio

Esta interfaz implementa las otras 3 interfaces que son de tipo generico es por esto que se les agrega el <T> al mismo tiempo que decimos que es una interfaz generica.

```Java
package repositorio;

import modelo.BaseEntity;

public interface OrdenablePaginableCrudRepositorio<T> extends CrudRepositorio<T>, OrdenableRepositorio<T>, PaginableRepositorio<T>{

}

```

> **Note** recordar que en interfaces para decir que implementa o hereda de **otras interfaces** usamos `extends` en lugar de `implements`.

## Creacion de clase abstracta que implementara metodos en comun

La clase abstracta que tenemos que crear sera la clase padre de todas las clases que queremos que simulen la base de datos y el CRUD.

Se crea esta clase para reutilizar codigo ya que hay metodos que van a ser totalmente iguales independientemente del tipo de dato y es aqui donde tendremos que definir que los tipos de datos generios que aceptara sera los que extiendan de nuestra clase POJO.

* calse abstracta

```java
package repositorio;

import modelo.BaseEntity;

import java.util.ArrayList;
import java.util.List;

public abstract class AbstractListRepositorio<T extends BaseEntity> implements OrdenablePaginableCrudRepositorio<T> {

    // PROPERTIES

    protected final List<T> dataSource;

    public AbstractListRepositorio() {
        this.dataSource = new ArrayList<>();
    }

    // METHODS

    // CrudRepositorio

    @Override
    public List<T> listar() {
        return this.dataSource;
    }

    @Override
    public T buscarPorId(Integer id) {
        T cliente = null;
        for (T cli : this.dataSource) {
            if (cli.getId().equals(id)) cliente = cli;
        }

        return cliente;
    }

    @Override
    public void crear(T cliente) {
        this.dataSource.add(cliente);
    }

    @Override
    public void eliminar(Integer id) {
        this.dataSource.remove(this.buscarPorId(id));
    }


    // PaginableRepositorio
    @Override
    public List<T> listar(int desde, int hasta) {
        return this.dataSource.subList(desde, hasta);
    }
}
```

> Como es una clase abstracta no necesita implementar todos los metodos de las interfaces, pero si las tendra que implementar la clase que herede de esta, en esta clase solamente estamos definiendo los metodos y sus funcionamientos que seran iguales para todas las clases hijas de esta.

## Clase Final

En esta clase haremos el funcionamiento de la base de datos con una lista y con los metodos en especifico de las interfaces.

```java
package repositorio;

import modelo.Cliente;

import java.util.ArrayList;
import java.util.List;

public class ClientesListRepositorio extends AbstractListRepositorio<Cliente> {

    // METHODS

    // CrudRepositorio

    @Override
    public void editar(Cliente updatedClient) {
        Cliente outdatedClient = this.buscarPorId(updatedClient.getId());
        outdatedClient.setNombre(updatedClient.getNombre());
        outdatedClient.setApellido(updatedClient.getApellido());
    }


    // OrdenableRepositorio
    @Override
    public List<Cliente> listar(String campo, Direccion direccion) {
        List<Cliente> listaClientes = new ArrayList<>(this.dataSource);

        listaClientes.sort((o1, o2) -> {
            int resultado = 0;
            if (Direccion.ASC.equals(direccion)) {
                resultado = ordenar(campo, o1, o2);
            } else if (Direccion.DESC.equals(direccion)) {
                resultado = ordenar(campo, o2, o1);
            }
            return resultado;
        });

        return listaClientes;
    }

    private int ordenar(String campo, Cliente c1, Cliente c2) {
        int resultado = 0;
        switch (campo) {
            case "id" -> resultado = c1.getId().compareTo(c2.getId());
            case "nombre" -> resultado = c1.getNombre().compareTo(c2.getNombre());
            case "apellido" -> resultado = c1.getApellido().compareTo(c2.getApellido());
        }
        return resultado;
    }

}
```

en esta clase final ya no tenemos que definir todos los metodos de las interfaces ya que el funcionamiento de varios metodos estan implementados en la clase abstracta.

Por lo tanto si queremos crear otra clase que simule una base de datos y su Crud solamente tenemos que crear otra clase de tipo de dato que herede de BaseEntity y otra clase final donde solamente se crearan 2 metodos personalizados y es todo, por lo que queda muy reutilizable el codigo.
