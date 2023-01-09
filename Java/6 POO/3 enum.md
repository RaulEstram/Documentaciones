# Enum

Los enum (enumeraciones) son un tipo de dato especial en Java que se utiliza para representar un conjunto de valores constantes. Son muy útiles en casos en los que quieres limitar los valores posibles de una variable a un conjunto conocido de opciones.

Por ejemplo, supongamos que estás escribiendo una aplicación que maneja el estado de un pedido en una tienda en línea. Podrías usar un enum para representar los posibles estados del pedido, como "En espera", "En proceso" y "Enviado". Esto te permitiría asegurarte de que sólo se puedan asignar estos valores específicos a la variable de estado del pedido, en lugar de cualquier otro valor.

En general, se recomienda usar enum en Java cuando tienes un conjunto limitado y conocido de valores que quieres asignar a una variable. Esto puede ayudar a evitar errores y a mejorar la legibilidad del código, ya que los enum proporcionan una forma clara y concisa de representar estos valores. Sin embargo, es importante tener en cuenta que los enum no son adecuados para todos los casos y debes evaluar si son la mejor opción para tu aplicación en particular.

Ejemplo basico de un enum: 

```java
public enum Color {
    ROJO("Rojo"),
    ARENA("Arena"),
    AZUL("Azul"),
    BLANCO("Blanco"),
    NEGRO("Negro");

    private final String color;

    Color(String color) {
        this.color = color;
    }

    public String getColor() {
        return color;
    }

    @Override
    public String toString() {
        return "Color{" +
                "color='" + color + '\'' +
                '}';
    }
}
```

## Enum con varios argumentos

```java
public enum TipoAutomovil {

    PICKUP("PickUp", 2, "Auto pequeño y barato"),
    VMW("vmw", 4, "Auto de lujo"),
    CONVERTIBLE("Convertible", 2, "Auto deportivo");

    private final String nombre;
    private final int numeroPuerta;
    private final String description;


    TipoAutomovil(String nombre, int numeroPuerta, String description) {
        this.nombre = nombre;
        this.numeroPuerta = numeroPuerta;
        this.description = description;
    }

    public String getNombre() {
        return nombre;
    }

    public int getNumeroPuerta() {
        return numeroPuerta;
    }

    public String getDescription() {
        return description;
    }

    @Override
    public String toString() {
        return "TipoAutomovil{" +
                "nombre='" + nombre + '\'' +
                ", numeroPuerta=" + numeroPuerta +
                ", descripcion='" + description + '\'' +
                '}';
    }
}
```

## uso de enum con switch

```java
public class Main {
    public static void main(String[] args) {
        
        TipoAutomovil tipo = TipoAutomovil.CONVERTIBLE;

        switch (tipo) {
            case VMW -> System.out.println("es vmw");
            case CONVERTIBLE -> System.out.println("es convertible");
            case PICKUP -> System.out.println("es converitble");
        }

    }
}
```

## iterar un enum

```java
public class Main {
    public static void main(String[] args) {

        TipoAutomovil[] tipos = TipoAutomovil.values();

        for (TipoAutomovil tipo : tipos) {
            System.out.println(tipo.name() + " = " + tipo);
        }

    }
}
```