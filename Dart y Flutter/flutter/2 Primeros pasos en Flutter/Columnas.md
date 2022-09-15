# Columnas

Las columnas serán algo importante dentro de nuestras aplicaciones para acomodar widgets, es por esto que tenemos la clase **Colum**.

Esta clase nos servirá para agregar varios widgets es por esto que **en lugar de child usaremos children**.

Par agregar varios widgets en la propiedad **children** le pasaremos una lista de **Widget**.

Un ejemplo seria el siguiente: 


```dart
import 'package:flutter/material.dart';

class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
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

En el anterior código podemos ver que usamos la clase **Column** en el hijo del cuerpo de nuestro objeto **Scaffold**.

Tambien podemos apreciar que le agregamos las siguientes cosas:

* le pasamos una lista de **Widget** en su propiedad **Children** para definir los Widgets que tendra
* Usamos **mainAxisAlignment** para definir en que parte estarán los widgets en el eje y.
* Usamos **crossAxisAlignment** para definir en que parte estarán los widgets en el eje x (dentro del tamaño maximo del widget con mayor width)

> **Note** más informacion de la clase Column [aqui](https://api.flutter.dev/flutter/widgets/Column-class.html)