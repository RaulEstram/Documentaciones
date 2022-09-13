# StatefulWidget

Los **StatefulWidget** nos sirven cuando necesitamos que la interfaz se redibuje porque algo va a cambiar.

Para usar uno tenemos que crear una clase que herede de este tipo de widgets y otra de **State**, esto nos servirá para que cuando usemos la función **setState((){})** se pueda redibujar todo.

un ejemplo seria el siguiente:

```dart
import 'package:flutter/material.dart';

class CounterScreen extends StatefulWidget {
  const CounterScreen({super.key});

  @override
  State<CounterScreen> createState() => _CounterScreenState();
}

class _CounterScreenState extends State<CounterScreen> {
  int count = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.pink,
        title: const Center(
            child: Text(
          "CounterScreen",
          style: TextStyle(fontWeight: FontWeight.bold, fontSize: 25),
        )),
        elevation: 0,
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          crossAxisAlignment: CrossAxisAlignment.center,
          children: <Widget>[
            const Text(
              'Numero de clicks',
              style: TextStyle(
                  fontFamily: "Roboto",
                  fontSize: 40,
                  fontWeight: FontWeight.bold),
            ),
            Text(
              '$count',
              style: const TextStyle(
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
        onPressed: () {
          count++;
          setState(() {});
        },
        child: const Icon(
          Icons.add,
          size: 40,
        ),
      ),
    );
  }
}
```

**setState((){})** Notifica al framework que un estado interno del objeto cambio y que redibuje al objeto, y se le tiene que pasar una función, en este caso una función anónima que no hace nada, ya que los cambios se hicieron afuera, pero podrían hacerse dentro de este método.

> **Note** Podemos empezar a trabajar con **statelessWidget** y cuando necesitemos que algo se redibuje usamos "Ctrl + ." y cambiamos nuestra clase a una con **statefulWidget**.

> **Warning** A pesar de que podemos usar statefulWidget se recomienda que trabajemos con statelessWidget siempre que se pueda, ya que también tiene sus formas para redibujar elementos.