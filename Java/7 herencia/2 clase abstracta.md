# Clases abstractas

Una clase abstracta en Java es una clase que no puede ser instanciada directamente. **Una clase abstracta se utiliza como base para otras clases, proporcionando una estructura y un comportamiento común. **

Una clase abstracta puede tener métodos abstractos, que son métodos que no tienen implementación y deben ser implementados por las clases hijas. También pueden tener métodos con implementación, que pueden ser reutilizados por las clases hijas. 

Es necesario extender una clase abstracta para poder crear objetos de ella.

## Importancia 

Las clases abstractas en Java sirven principalmente para proporcionar una estructura y un comportamiento común a varias clases relacionadas. Al crear una clase abstracta, se pueden definir métodos y propiedades que son comunes a todas las clases que heredan de ella, lo que permite la reutilización de código y la organización de una jerarquía de clases.

Algunas de las principales ventajas de utilizar clases abstractas son:

* Permite la creación de jerarquías de clases: Una clase abstracta puede ser utilizada como base para otras clases, lo que permite la organización de una jerarquía de clases.

* Proporciona una estructura común: Al definir una clase abstracta, se pueden establecer los métodos y propiedades que son comunes a todas las clases que heredan de ella, lo que proporciona una estructura común.

* Ayuda a la reutilización de código: Al crear una clase abstracta, se pueden definir métodos con implementación que pueden ser reutilizados por las clases hijas, lo que ayuda a reducir la cantidad de código necesario.

* Permite la implementación de polimorfismo: Al utilizar clases abstractas se pueden crear objetos de diferentes clases que heredan de ella y tratarlos de manera genérica como si fueran de la clase abstracta

* Permite la creación de clases incompletas : Es posible crear clases que no pueden ser instanciadas, pero que proporcionan una estructura básica y un comportamiento común para otras clases.

## Ejemplo

```java
package com.teamuwu.appforms.form.elements;

abstract public class ElementoForm {

    protected String nombre;
    protected String valor;

    // CONSTRUCTURES
    public ElementoForm() {
    }

    public ElementoForm(String nombre) {
        this();
        this.nombre = nombre;
    }

    abstract public String dibujarHtml();

    public void setValor(String valor) {
        this.valor = valor;
    }
}

```

```java
package com.teamuwu.appforms.form.elements;

public class InputForm extends ElementoForm {

    // PROPIEDADES
    private String tipo = "text";

    // CONSTRUCTORES
    public InputForm(String nombre) {
        super(nombre);
    }

    public InputForm(String nombre, String tipo) {
        super(nombre);
        this.tipo = tipo;
    }

    // MÉTODOS
    @Override
    public String dibujarHtml() {
        return "<input type=\"" + this.tipo +
                "\" name=\"" + this.nombre +
                "\" values=\"" + this.valor + "\">";
    }

    // GETTERS & SETTERS
    public String getTipo() {
        return tipo;
    }

    public void setTipo(String tipo) {
        this.tipo = tipo;
    }
}
```