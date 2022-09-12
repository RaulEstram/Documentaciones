# Separando la logica en varios Archivos

Es absurdo creer que toda la lógica de nuestra aplicación estará en un solo archivo, por lo que vamos a ver como distribuirla en varios archivos.

Para hacer esto, podemos crear todos los directorios y subdirectorios que necesitemos dentro de la carpeta **lib**.

De esta forma podemos generar todas las clases/widgets que necesitemos para distribuir la lógica de nuestro programa en diferentes archivos.

Para esto veamos el siguiente ejemplo:


* screens/home_screen.dart

```dart
import 'package:flutter/cupertino.dart';

class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return const Center(
      child: Text('Home Screen.'),
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
    return const MaterialApp(home: HomeScreen());
  }
}
```


> **Note** se recomienta que los archivos tengan el nombre en sneak lower case, ejemplo: archivo_nombre_ejemplo.dart

> **Note** El Key nos sirve para identificar un widget o este widget dentro del contexto, y es probable que en muchas aplicaciones nunca lo utilicemos, pero es una buena práctica de programación en flutter y es por esto que lo tenemos que agregar.