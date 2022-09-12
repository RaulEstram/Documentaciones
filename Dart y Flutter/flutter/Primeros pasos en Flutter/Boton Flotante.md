# Botón Flotante

Los botones flotantes son una posibilidad gracias a la clase **Scaffold**.

Para definir un boton flotante utilizamos la propiedad **floatingActionButton** el cual espera un **Widget**, en este caso, usaremos **FloatingActionButton**.

Este widget tiene algunas propieades como:

* ```backgroundColor``` para el color del botón.
* ```elevation``` para elevar el botón y que tenga sombra.
* ```onPressed``` para darle la función que ejecutara al presionar el botón.
* ```child``` para darle un widget como hijo, que generalmente será un **Icon**.

También tenemos otra propiedad de la clase **Scaffold** como el **floatingActionButtonLocation** para determinar la localización del botón flotante.

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
      floatingActionButtonLocation: FloatingActionButtonLocation.centerFloat,
      floatingActionButton: FloatingActionButton(
        backgroundColor: Colors.pink[400],
        elevation: 10,
        onPressed: () => {},
        child: const Icon(
          Icons.add,
          size: 40,
        ),
      ),
    );
  }
}
```


