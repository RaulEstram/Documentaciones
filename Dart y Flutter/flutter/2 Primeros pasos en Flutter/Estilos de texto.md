# Estilos de Texto

Para agregarle estilos a nuestros textos en flutter usaremos la clase **Text** donde podremos modificar sus propiedades para darle el estilo que queramos al texto.

Algunas propiedades que podemos modificar serian:

* ```style``` para el estilo en general (style es una clase diferente que tiene sus propias propiedades)



Un ejemplo seria: 

```dart
import 'package:flutter/material.dart';

class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.pink,
        title: const Center(
            child: Text(
          "HomeScreen",
          style: TextStyle(fontWeight: FontWeight.bold, fontSize: 25),
        )),
        elevation: 0,
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          crossAxisAlignment: CrossAxisAlignment.center,
          children: const <Widget>[
            Text(
              'Numero de clicks',
              style: TextStyle(
                  fontFamily: "Roboto",
                  fontSize: 40,
                  fontWeight: FontWeight.bold),
            ),
            Text(
              '10',
              style: TextStyle(
                  color: Colors.pink,
                  fontFamily: "Roboto",
                  fontSize: 35,
                  fontWeight: FontWeight.bold),
            ),
          ],
        ),
      ),
    );
  }
}

```


> **Note** más informacion de la clase Text [aqui](https://api.flutter.dev/flutter/widgets/Text-class.html)