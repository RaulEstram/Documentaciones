# AppBar

El **AppBar** en pocas palabras nos sirve para definir el "header" de nuestra app.

El **AppBar** tiene algunas propiedades como son:

* **elevation** que nos sirve para definir la elevación del appbar, lo que provoca que tenga una sombra.
* **title** que nos sirve para definir el titulo del **AppBar**
* **backgroundColor** que nos sirve para definir el color de fondo de nuestro **AppBar**  

Un ejemplo seria el siguiente:


```dart
import 'package:flutter/material.dart';

class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.pink,
        title: const Center(child: Text("HomeScreen")),
        elevation: 0,
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          crossAxisAlignment: CrossAxisAlignment.center,
          children: const <Widget>[
            Text('Numero de clicks'),
            Text('10'),
          ],
        ),
      ),
    );
  }
}
```

> **Note** más informacion de la clase AppBar [aqui](https://api.flutter.dev/flutter/material/AppBar-class.html)