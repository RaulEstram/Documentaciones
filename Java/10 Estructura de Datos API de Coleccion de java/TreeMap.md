# TreeMap

por defecto va a ordenar por las llaves, y al igual que los TreeSet podemos pasarle otro tipo de formas para ordenarlo.

```java
package elementos.map;

import java.util.*;

public class EjemploHashMap {

    public static void main(String[] args) {

        Map<String, Object> persona = new TreeMap<>();

        persona.put("nombre", "Raul");
        persona.put("apellido", "Estrada");
        persona.put("email", "raulestrada2000@outlook.com");

        System.out.println("persona = " + persona);

        Map<String, String> direccion = new HashMap<>();
        direccion.put("calle", "calle paquita la del barrio");
        direccion.put("colonia", "olle no lo sé no soy 100tifico");

        persona.put("direccion", direccion);

        System.out.println("persona = " + persona);

    }

}
```

* ordenar diferente

```java
package elementos.map;

import javax.swing.*;
import java.util.*;

public class EjemploHashMap {

    public static void main(String[] args) {
        // manual
        // Map<String, Object> persona = new TreeMap<>((a,b) -> b.compareTo(a));
        // usanod Comparator
        Map<String, Object> persona = new TreeMap<>(Comparator.reverseOrder());
        //Map<String, Object> persona = new TreeMap<>(Comparator.naturalOrder());

        persona.put("nombre", "Raul");
        persona.put("apellido", "Estrada");
        persona.put("email", "raulestrada2000@outlook.com");

        System.out.println("persona = " + persona);

        Map<String, String> direccion = new HashMap<>();
        direccion.put("calle", "calle paquita la del barrio");
        direccion.put("colonia", "olle no lo sé no soy 100tifico");

        persona.put("direccion", direccion);

        System.out.println("persona = " + persona);

    }

}
```