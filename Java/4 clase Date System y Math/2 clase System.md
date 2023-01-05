# System

System nos da varias cosas del sistema por ejemplo sus propiedades las cuales podemos utilizar con **System.getProperty("key)**:

```java
import java.util.Properties;

public class Main {
    public static void main(String[] args) {

        String username = System.getProperty("user.name");
        System.out.println("username = " + username);

        String home = System.getProperty("user.home");
        System.out.println("home = " + home);
        
        String workspace = System.getProperty("user.dir");
        System.out.println("workspace = " + workspace);

        String java = System.getProperty("java.version");
        System.out.println("java = " + java);

        String lineSeparator = System.getProperty("line.separator");
        System.out.println("lineSeparator = " + lineSeparator);

        String lineSeparator2 = System.lineSeparator();
        System.out.println("lineSeparator2 = " + lineSeparator2);

        // imprimir todas las propiedades del sistema
        Properties p = System.getProperties();
        p.list(System.out);
        
    }

}
```

## Crear nuestras propias propiedades de sistema

Para crear nuestras propias propiedades de sistema tenemos que crear un archivo con terminacion **.properties**

un ejemplo seria el siguiente:

> config.properties

```
config.puerto.servidor=8090
config.puerto.nombre=servidor trabajo
config.env.key=jdslñkif54hlafdhg 54879fksjg
config.env.password=password123
```

> **Note**: no se usarn comillas para los strings ni para los numeros, es tal cual el ejemplo

Una vez creado el archivo con nuestras propiedades podemos usar el siguiente codigo de ejemplo para cargar las propiedades al sistema y de esta manera poder utilizarlas.

```java
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.util.Properties;

public class Main {
    public static void main(String[] args) {
        try {
            // creamos un FileInputStream para cargar el archivo config.properties
            FileInputStream archivo = new FileInputStream("src/config.properties");
            // creamos un Properties para cargar todas las propiedades del sistema
            Properties p = new Properties(System.getProperties());
            // cargamos a nuestra instancia de Properties las propiedades de nuestro archivo config.properties con la
            // instancia de la clase FileInputStream
            p.load(archivo);
            // podemos agregar nuestras propiedades a nuestra instancia de Properties con setProperty
            p.setProperty("config.ejemplo", "ejemplo jsjsjs salu2");
            // Cargamos las propiedades de nuestra instancia de Properties a las propiedades de nuestro sistema
            System.setProperties(p);
            // ahora podemos utilizar las propiedades de nuestro archivo config.properties
            System.out.println(System.getProperty("config.puerto.servidor"));
            System.out.println(System.getProperty("config.puerto.nombre"));
        } catch (FileNotFoundException e) {
            System.out.println("Error al encontrar el archivo con las propiedades :c");
        } catch (IOException e) {
            System.out.println("Error al cargar las propiedades :c");

        }
    }

}
```

## Obtener las variables de entorno o ambiente

Cualquier sistema operativo tiene sus propias variables de entorno o de ambiente, y en java los podemos obtener con **System.getenv()** ya sea especificando el key dentro de los "()" o sin definirlo para obtener un Map con todas las vairables de entorno con su respectivo valor.

```java
import java.util.Map;

public class Main {
    public static void main(String[] args) {
        // obtenemos las variables de ambiente o de entorno del sistema
        Map<String, String> entorno = System.getenv();
        System.out.println("entorno.toString() = " + entorno.toString());

        // iterar Map
        for (String key :entorno.keySet()) {
            System.out.println("key = " + key + " -> " + entorno.get(key));
        }


        // obtener una variable de entorno
        String username = System.getenv("USERNAME");
        System.out.println("username = " + username);
        String user = System.getenv("LOGNAME");
        System.out.println("user = " + user);
        String home = System.getenv("HOME");
        System.out.println("home = " + home);

        // obtener una variable de entorno 2
        String path = entorno.get("PATH");
        System.out.println("path = " + path);

    }

}
```


## Otras caracteristicas y funciones utiles

tenemos algunas funciones utilies como:

* **System.exit(1)** para parar el proceso, termina la aplicacion si hay un error, si todo sale bien se utiliza un **0**.
* **main(args)** para volver a repetir todo el codigo.
* **System.gc** eliminamos todos las instancias que no se esten utilizando para liberar espacio, y memoria (estamos acelerando el proceso que se hacer de forma automaticamente).

## Clase Runtime

La clase Runtime una de sus funcionalidades es que podemos ejecutar aplicaiones con este, un ejemplo a continuacion:

```java
public class Main {
    public static void main(String[] args) {

        // ejemplo de programa para ejecutar un programa del sistema operativo
        // Runtime nos permite ejecutar aplicaciones por ejemplo
        // creamos una instancia de Runtime
        Runtime rt = Runtime.getRuntime();
        Process proceso;
        System.out.println(System.getProperty("os.name"));
        try {
            if (System.getProperty("os.name").startsWith("Windows")) {
                proceso = rt.exec("notepad");
            } else {
                proceso = rt.exec("brave-browser");
            }
            proceso.waitFor();
        } catch (Exception e) {
            System.err.println("El comando es desconocido: " + e.getMessage());
            System.exit(1);
        }

        System.out.println("se cerro");

    }
}
```