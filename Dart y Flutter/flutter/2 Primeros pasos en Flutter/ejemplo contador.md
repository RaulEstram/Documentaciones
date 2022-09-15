# Contador

A continuacion se muestra el codigo para crear un contador en dart.

* main.dart

```dart
import 'package:contador/screens/counter_screen.dart';
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      debugShowCheckedModeBanner: false,
      home: CounterScreen(),
    );
  }
}
```

* lib/screens/counter_screen.dart

```dart
import 'dart:io';

import 'package:flutter/material.dart';

class CounterScreen extends StatefulWidget {
  const CounterScreen({super.key});

  @override
  State<CounterScreen> createState() => _CounterScreenState();
}

class _CounterScreenState extends State<CounterScreen> {
  int count = 0;

  void increase() => setState(() => count++);
  void decrease() => setState(() => count--);
  void reset() => setState(() => count = 0);

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
      floatingActionButton: CustomFloatingButtonsActions(
          increase: increase, decrease: decrease, reset: reset),
    );
  }
}

class CustomFloatingButtonsActions extends StatelessWidget {
  final Function increase;
  final Function decrease;
  final Function reset;

  const CustomFloatingButtonsActions({
    required this.increase,
    required this.decrease,
    required this.reset,
    Key? key,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Row(
      mainAxisAlignment: MainAxisAlignment.spaceEvenly,
      children: [
        FloatingActionButton(
          backgroundColor: Colors.pink[400],
          onPressed: () => decrease(),
          child: const Icon(Icons.remove, size: 40),
        ),
        FloatingActionButton(
          backgroundColor: Colors.pink[400],
          onPressed: () => reset(),
          child: const Icon(Icons.clear, size: 40),
        ),
        FloatingActionButton(
          backgroundColor: Colors.pink[400],
          onPressed: () => increase(),
          child: const Icon(Icons.add, size: 40),
        ),
      ],
    );
  }
}
```