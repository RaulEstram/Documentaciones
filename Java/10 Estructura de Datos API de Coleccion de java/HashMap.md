# HashMap

Veamos un ejemplo basico del uso de HashMap.

```java
package elementos.map;

import java.util.*;

public class EjemploHashMap {

    public static void main(String[] args) {

        Map<String, String> persona = new HashMap<>();

        persona.put("nombre", "Raul");
        persona.put("apellido", "Estrada");
        persona.put("email", "raulestrada2000@outlook.com");

        System.out.println("persona = " + persona);
        
        // obtener un valor mediante llave
        System.out.println("persona.get(\"nombre\") = " + persona.get("nombre"));
        
        // obtener llaves y valores
        System.out.println("persona.keySet() = " + persona.keySet());
        System.out.println("persona.values() = " + persona.values());

        // eliminar, puede ser mediante key o key con valor, key con objeto

        System.out.println("persona.remove(\"email\"); = " + persona.remove("email"));
        
        // remplazar el valor de una key o remplazar un key con un valor en específico con otro valor

        System.out.println("persona.replace(\"nombre\", \"setch\"); = " + persona.replace("nombre", "setch"));

        System.out.println("persona = " + persona);
        
        // si contiene un valor o key en especifico

        System.out.println("persona.containsKey(\"nombre\") = " + persona.containsKey("nombre"));
        System.out.println("persona.containsValue(\"Estrada\") = " + persona.containsValue("Estrada"));

        // iterar un map chido

        for (Map.Entry<String, String> par: persona.entrySet()){
            System.out.println("par.getKey() = " + par.getKey());
            System.out.println("par.getValue() = " + par.getValue());
        }

        persona.forEach((llave, valor) -> System.out.println(llave + ": " + valor));
    }

}
```

## HashMap con otros objetos


```java
package elementos.map;

import java.util.*;

public class EjemploHashMap {

    public static void main(String[] args) {

        Map<String, Object> persona = new HashMap<>();

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