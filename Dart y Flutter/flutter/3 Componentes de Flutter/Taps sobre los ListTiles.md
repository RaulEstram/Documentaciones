# Taps sobre los ListTiles

Para realizar Taps sobre los **ListTiles** y que ejecuten una función, usaremos la propiedad **onTap** como se muestra a continuación: 


```dart
import 'package:flutter/material.dart';

class Listview2Screen extends StatelessWidget {
  const Listview2Screen({Key? key}) : super(key: key);

  final List<String> elementos = const ["Mangos", "Manzanas", "Uvas", "Kiwi"];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Listview2Screen'),
        elevation: 0,
        backgroundColor: Colors.pink[300],
      ),
      body: ListView.separated(
          itemBuilder: (_, index) {
            return ListTile(
              leading: const Icon(Icons.grade, color: Colors.pink),
              title: Text(elementos[index]),
              trailing: const Icon(Icons.arrow_forward_ios_rounded),
              onTap: () {
                print("hola");
              },
            );
          },
          separatorBuilder: (_, __) => const Divider(),
          itemCount: elementos.length),
    );
  }
}
```