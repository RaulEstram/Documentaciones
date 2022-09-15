# Listview y ListTitles

Tanto los **Listview y ListTitles** nos servirán para crear listas en flutter.

Los **Listview** serán la lista y los **ListTitles** los elementos de la lista.

Hay 3 principales formas para crear listas en flutter con estas clases que serian:

* con **Listview()**
* con **Listview.separated()** (Recomendada)
* con **Listview.builder()** (Recomendada)

## Listview()

Para esta forma de crear listas tenemos que pasarle una lista de Widgets a la propiedad children de nuestro objeto ListView.

A continuación un ejemplo:

```dart
import 'package:flutter/material.dart';

class Listview1Screen extends StatelessWidget {
  const Listview1Screen({Key? key}) : super(key: key);

  final List<String> elementos = const ["Mangos", "Manzanas", "Uvas", "Kiwi"];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Listview1Screen'),
      ),
      body: ListView(
        children: <Widget>[
          ...elementos
              .map((e) => ListTile(
                  title: Text(e),
                  trailing: const Icon(Icons.arrow_forward_ios_rounded)))
              .toList()
        ],
      ),
    );
  }
}
```

## **Listview.separated()**

Esta forma es más fácil de implementar que la anterior.

Veamos el siguiente ejemplo:

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
      ),
      body: ListView.separated(
          itemBuilder: (_, index) {
            return ListTile(
              leading: const Icon(Icons.grade),
              title: Text(elementos[index]),
              trailing: const Icon(Icons.arrow_forward_ios_rounded),
            );
          },
          separatorBuilder: (_, __) => const Divider(),
          itemCount: elementos.length),
    );
  }
}
```

Como se puede apreciar en el anterior código, al utilizar **ListView.separated()** tenemos que agregar **itemBuilder, separatorBuilder e itemCount** donde:

* ```itemBuilder``` es el widget que tendrá la lista, en estos casos un **ListTitle**.

* ```separatorBuilder``` es el separador de los widgets en la lista.

* ```itemCount``` es el número de widgets que tendrá la lista, en este caso, el tamaño de la lista.

## Listview.builder()

Es lo **mismo** que **Listview.separated**, pero **sin** el **separatorBuilder**

---

> **Note** Más informacion de ListView [aquí](https://api.flutter.dev/flutter/widgets/ListView-class.html) o de ListTile [aquí](https://api.flutter.dev/flutter/material/ListTile-class.html)