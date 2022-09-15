# Inicio de proyecto contador y hola mundo

Para empezar tenemos que crear un proyecto nuevo de Flutter y probar que funcione adecuadamente

## Nuestro primer Widget

Lo que vamos hacer es eliminar todo el codigo del archivo **main.dart** en la carpeta **lib**.

Esto con el fin de ir creando paso a paso nuestra aplicacion de contador propia.

El codigo que vamos a utilizar es el siguiente:

```dart
import 'package:flutter/material.dart';

void main(){
  runApp(MyApp());
}

class MyApp extends StatelessWidget{

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Center(
        child: Text('Hola perro.'),
      ),
    );
  }

}
```


El código anterior, a pesar de ser funcional, después se verá como mejorarlo.

Podemos apreciar que importamos un paquete llamado **material** el cual importa varios widgets que estarán disponibles para su uso en nuestra aplicación.

Después tenemos la función **main** que como sabemos todas las aplicaciones o programas en dart tienen que llevar esta función y no es la excepción al utilizar flutter.

Dentro de la función **main** estamos diciendo que vamos a correr nuestra aplicación, la cual tiene el nombre **MyApp**, en esta parte lo que estamos pasando como argumento es una instancia de clase, por lo que podríamos usar la sintaxis de **new MyApp()** o **MyApp()** (es preferible usar la segunda forma).

Por ultimo nos encontramos con la clase **MyApp** que hereda de **StatelessWidget** que es uno de los 2 tipos de Widgets que hay en flutter, por lo que la clase **MyApp** es en realidad un **Widget**

En esta clase encontramos el método **build**, que es un método que se tiene que crear al crear un nuevo widget que hereda de **StatelessWidget o StatefulWidget**.

El método **build** como lo indica, regresa un Widget, en este caso retorna una instancia de **MaterialApp**.


> **Note** Documentación de la clase **MaterialApp** [aquí](https://api.flutter.dev/flutter/material/MaterialApp-class.html)


## MaterialApp

Es un widget de conveniencia que envuelve una serie de widgets que comúnmente se requieren para las aplicaciones de Material Design.


```dart
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Center(
        child: Text('Hola perro.'),
      ),
    );
  }
```

Dentro de la instancia de **MaterialApp** que regresamos en la función **build** tenemos la palabra reservada **home**.

**home** es el widget para la ruta predeterminada de la aplicación.

Por otro lado, tenemos la clase **Center** como valor de **home** el cual crea un widget que centra a su hijo.

Por último, vemos que el hijo del widget **Center** lo definimos con la palabra reservada **child** el cual contienen un widget llamado **Text**, este widget muestra una cadena de texto con un solo estilo.

