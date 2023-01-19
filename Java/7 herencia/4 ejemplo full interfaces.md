#  ejemplo de uso de muchas interfaces

este es un ejemplo de uso de varias interfaces:

* modelo/Cliente

```java
package modelo;

import java.util.Objects;

public class Cliente {

    // PROPRIETIES
    private final Integer id;
    private String nombre, apellido;
    private static int ultimoId;

    // CONSTRUCTORS
    public Cliente() {
        this.id = ++ultimoId;
    }

    public Cliente(String nombre, String apellido) {
        this();
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


    public Integer getId() {
        return id;
    }

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

* repositorio/PaginableRepositorio

```java
package repositorio;

import modelo.Cliente;

import java.util.List;

public interface PaginableRepositorio {

    List<Cliente> listar(int desde, int hasta);

}
```

* repositorio/OrdenableRepositorio

```java
package repositorio;

import modelo.Cliente;

import java.util.List;

public interface OrdenableRepositorio {

    List<Cliente> listar(String campo, Direccion direccion);

}
```

* repositorio/CrudRepositorio

```java
package repositorio;

import modelo.Cliente;
import java.util.List;

public interface CrudRepositorio {

    List<Cliente> listar();

    Cliente buscarPorId(Integer id);

    void crear(Cliente cliente);

    void editar(Cliente cliente);

    void eliminar(Integer id);

}
```

* repositorio/OrdenablePaginableCrudRepositorio

```java
package repositorio;

public interface OrdenablePaginableCrudRepositorio extends CrudRepositorio, OrdenableRepositorio, PaginableRepositorio{

}

```

* repositorio/Direccion

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

* repositorio/ClientesListRepositorio

```java
package repositorio;

import modelo.Cliente;

import java.util.ArrayList;
import java.util.List;

public class ClientesListRepositorio implements OrdenablePaginableCrudRepositorio {

    // PROPERTIES

    private final List<Cliente> dataSource;

    public ClientesListRepositorio() {
        this.dataSource = new ArrayList<>();
    }

    // METHODS

    // CrudRepositorio

    @Override
    public List<Cliente> listar() {
        return this.dataSource;
    }

    @Override
    public Cliente buscarPorId(Integer id) {
        Cliente cliente = null;
        for (Cliente cli : this.dataSource) {
            if (cli.getId().equals(id)) cliente = cli;
        }

        return cliente;
    }

    @Override
    public void crear(Cliente cliente) {
        this.dataSource.add(cliente);
    }

    @Override
    public void editar(Cliente updatedClient) {
        Cliente outdatedClient = this.buscarPorId(updatedClient.getId());
        outdatedClient.setNombre(updatedClient.getNombre());
        outdatedClient.setApellido(updatedClient.getApellido());
    }

    @Override
    public void eliminar(Integer id) {
        this.dataSource.remove(this.buscarPorId(id));
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

    /*
    // OrdenableRepositorio
    @Override
    public List<Cliente> listar(String campo, Direccion direccion) {
        List<Cliente> listaClientes = new ArrayList<>(this.dataSource);
        listaClientes.sort(new Comparator<>() {
            @Override
            public int compare(Cliente o1, Cliente o2) {
                int resultado = 0;
                if (Direccion.ASC.equals(direccion)) {
                    resultado = ordenar(o1, o2);
                } else if (Direccion.DESC.equals(direccion)) {
                    resultado = ordenar(o2, o1);
                }
                return resultado;
            }

            private int ordenar(Cliente c1, Cliente c2) {
                int resultado = 0;
                switch (campo) {
                    case "id" -> resultado = c1.getId().compareTo(c2.getId());
                    case "nombre" -> resultado = c1.getNombre().compareTo(c2.getNombre());
                    case "apellido" -> resultado = c1.getApellido().compareTo(c2.getApellido());
                }
                return resultado;
            }
        });

        return listaClientes;
    }
    */


    /*
    @Override
    public List<Cliente> listar(String campo, Direccion direccion) {
        List<Cliente> listaClientes = new ArrayList<>(this.dataSource);
        listaClientes.sort((o1, o2) -> {

            int resultado = 0;

            if (Direccion.ASC == direccion) {
                switch (campo) {
                    case "id" -> resultado = o1.getId().compareTo(o2.getId());
                    case "nombre" -> resultado = o1.getNombre().compareTo(o2.getNombre());
                    case "apellido" -> resultado = o1.getApellido().compareTo(o2.getApellido());
                }
            } else if (Direccion.DESC == direccion) {
                switch (campo) {
                    case "id" -> resultado = o2.getId().compareTo(o1.getId());
                    case "nombre" -> resultado = o2.getNombre().compareTo(o1.getNombre());
                    case "apellido" -> resultado = o2.getApellido().compareTo(o1.getApellido());
                }
            }

            return resultado;
        });
        return listaClientes;
    }
    */

    /*
     @Override
    public List<Cliente> listar(String campo, Direccion direccion) {
        this.dataSource.sort(new Comparator<Cliente>() {
            @Override
            public int compare(Cliente o1, Cliente o2) {

                int resultado = 0;

                if (Direccion.ASC == direccion) {
                    switch (campo) {
                        case "id" -> resultado = o1.getId().compareTo(o2.getId());
                        case "nombre" -> resultado = o1.getNombre().compareTo(o2.getNombre());
                        case "apellido" -> resultado = o1.getApellido().compareTo(o2.getApellido());
                    }
                } else if (Direccion.DESC == direccion){
                    switch (campo) {
                        case "id" -> resultado = o2.getId().compareTo(o1.getId());
                        case "nombre" -> resultado = o2.getNombre().compareTo(o1.getNombre());
                        case "apellido" -> resultado = o2.getApellido().compareTo(o1.getApellido());
                    }
                }

                return resultado;
            }
        });
        return this.dataSource;
    }
     */

    // PaginableRepositorio
    @Override
    public List<Cliente> listar(int desde, int hasta) {
        return this.dataSource.subList(desde, hasta);
    }
}
```
