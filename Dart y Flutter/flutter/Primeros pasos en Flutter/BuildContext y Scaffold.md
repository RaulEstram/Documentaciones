# BuildContext y Scaffold

Estos 2 elementos son muy importantes en flutter es por esto que se definirán de forma básica a continuación.

## Scaffold

La clase de **Scaffold** implementa la estructura de diseño visual básica de Material Design.

Dentro de este widget tenemos palabras reservadas como **body** que sirve para definir el contenido principal del Scaffold.

Un ejemplo de su uso seria:

* screens/screen_home.dart

```dart
import 'package:flutter/material.dart';

class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return const Scaffold(
      body: Center(
        child: Text('Home Screen.'),
      ),
    );
  }
}
```

* main.dart

```dart
import 'package:flutter/material.dart';
import 'package:contador/screens/home_screen.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
        debugShowCheckedModeBanner: false, home: HomeScreen());
  }
}
```

> **Note** Para más información del widget **Scaffold** click [aquí](https://api.flutter.dev/flutter/material/Scaffold-class.html).


## BuildContext

Por otro lado el **BuildContext** es un identificador de la ubicación de un widget en el árbol de widgets.