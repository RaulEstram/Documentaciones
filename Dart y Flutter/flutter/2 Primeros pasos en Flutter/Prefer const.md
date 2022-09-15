# Prefer const

El **Prefer const** es una nueva característica que se agregó en las últimas versiones de flutter el cual ayuda a que nuestras aplicaciones sean más rápidas.

Esta característica nos dice que definamos las instancias de clases como constantes cada vez que su contenido nunca cambie.

La instancia que vayamos a definir como constante tiene que ser aquella de mayor nivel o que sea el padre de todos los widgets que no cambien, como es en el siguiente ejemplo:

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      home: Center(
        child: Text('Te Quiero Mucho.'),
      ),
    );
  }
}
```

En el anterior código podemos ver como usamos el **Prefer const** al crear la instancia de la clase **MyApp** en la función **runApp**, ya que no van a cambiar los widgets.

También lo utilizamos en el **return** del método **build**, ya que el **MaterialApp** y los Widgets que contiene no van a cambiar.