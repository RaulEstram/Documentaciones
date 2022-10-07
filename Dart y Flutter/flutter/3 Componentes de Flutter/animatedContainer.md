# Animated container

Es un elemento al cual se le puede asignar una animacion por lo que necesita algunas propiedades en especial como son: **Duration y Curve**

Un ejemplo seria:

```dart
import 'dart:math';

import 'package:flutter/material.dart';

class AnimatedScreen extends StatefulWidget {
  const AnimatedScreen({Key? key}) : super(key: key);

  @override
  State<AnimatedScreen> createState() => _AnimatedScreenState();
}

class _AnimatedScreenState extends State<AnimatedScreen> {
  double _width = 50;
  double _height = 50;
  Color _color = Colors.indigo;
  BorderRadius _borderRadius = BorderRadius.circular(10);

  void changeShape() {
    setState(() {
      Random random = Random();
      _width = random.nextInt(300).toDouble();
      _height = random.nextInt(300).toDouble();
      _color = Color.fromRGBO(
          random.nextInt(256), random.nextInt(256), random.nextInt(256), 1);
      _borderRadius = BorderRadius.circular(random.nextInt(100).toDouble());
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: const Text("Animated Container"),
        ),
        body: Center(
          child: AnimatedContainer(
              duration: const Duration(seconds: 1),
              curve: Curves.easeInOutQuart,
              height: _width,
              width: _height,
              decoration:
                  BoxDecoration(color: _color, borderRadius: _borderRadius)),
        ),
        floatingActionButton: FloatingActionButton(
          onPressed: () => changeShape(),
          child: const Icon(Icons.play_arrow),
        ));
  }
}

```