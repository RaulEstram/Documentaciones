# Cards

Una **Card** es un panel con esquinas ligeramente redondeadas y una sombra de elevación, que se utiliza para representar alguna información relacionada, por ejemplo, un álbum, una ubicación geográfica, una comida, detalles de contacto, etc.

Un ejemplo seria el siguiente:

```dart
import 'package:flutter/material.dart';

class CardScreen extends StatelessWidget {
  const CardScreen({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("Cards")),
      body: ListView(
        padding: const EdgeInsets.symmetric(vertical: 20, horizontal: 20),
        children: const [
          Card(
            child: ListTile(
              leading: Icon(Icons.photo),
              title: Text("Hoy un titulo"),
              subtitle: Text(
                  "Minim incididunt id irure excepteur ad sunt culpa elit in quis. Proident ullamco veniam et aliqua dolor et deserunt. Quis amet do consectetur quis esse est veniam consectetur do veniam exercitation. Ipsum sint mollit dolore amet ipsum sit. Nisi elit commodo id minim cupidatat quis do consequat. Dolor sunt enim aliqua eiusmod adipisicing amet eu Lorem nulla duis."),
            ),
          )
        ],
      ),
    );
  }
}

```

