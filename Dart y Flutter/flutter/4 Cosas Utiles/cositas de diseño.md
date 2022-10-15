# Cositas de diseño

Para que tengamos una idea de algunas cositas de diseño que pueden ser utiles si tenemos que crear alguna aplicacion con un diseño un poco mas complejo tenemos el siguiente ejemplo, donde vemos gradiantes, rotar widgets y posicionarlos.

```dart
import 'dart:math';
import 'package:flutter/material.dart';

class Background extends StatelessWidget {
  const Background({
    Key? key,
  }) : super(key: key);

  final boxDecoration = const BoxDecoration(
      gradient: LinearGradient(
          begin: Alignment.topLeft,
          end: Alignment.bottomRight,
          stops: [
        0.1,
        0.9
      ],
          colors: [
        Color(0xff2E305F),
        Color(0xff202333),
      ]));

  @override
  Widget build(BuildContext context) {
    return Stack(
      children: [
      // purple gradiant
      Container(
        decoration: boxDecoration,
      ),
      // pickbox
      const Positioned(
        top: -100,
        left: -60,
        child: _PinkBox())
    ]);
  }
}

class _PinkBox extends StatelessWidget {
  const _PinkBox({Key? key}) : super(key: key);
  
  @override
  Widget build(BuildContext context) {
    return Transform.rotate(
      angle: -pi / 4,
      child: Container(
        width: 360,
        height: 360, 
        decoration: BoxDecoration(
          color: Colors.pink,
          borderRadius: BorderRadius.circular(50),
          gradient: const LinearGradient(
            colors: [
              Color.fromRGBO(236, 98, 188, 1),
              Color.fromRGBO(241, 142, 172, 1)
            ]
          )
        ),
      ),
    );
  }
}
```

## BoxDecoration y gradient

**decoration** es una propiedad que tienen algunos widgets como **Container** el cual le podemos pasar un **BoxDecoration** que nos permite agregarle decoraciones a la caja de dicho widget.

Dentro de lo que podemos agregarle este el gradient.

En el ejemplo anterior tenemos el siguiente ejemplo:

```dart
final boxDecoration = const BoxDecoration(
    gradient: LinearGradient(
        begin: Alignment.topLeft,
        end: Alignment.bottomRight,
        stops: [
    0.1,
    0.9
    ],
        colors: [
    Color(0xff2E305F),
    Color(0xff202333),
]));
```

Donde definimos el tipo de gradient, de donde empieza y donde termina, los stops que es desde donde empieza y donde temina en cambio de colores y los colores.

> **Note** tambien tenemos el ejemplo de la siguiente propiedad ```borderRadius: BorderRadius.circular(50),``` que nos permitiria ddefinir que tan redondo queremos los bordes del contenedor.

## Rotar un widget.

Para rotar un widget tenemos que envolver la totalidad de este con el widget **Transform.rotate** el cual nos pedira un angle/angulo el cual tiene que usar "pi".

Un ejemplo del primer codigo seria:

```dart
return Transform.rotate(
      angle: -pi / 4,
      child: Container(...));
```

## Posicionar un Widget

si quisieramos posicionar un widget, primero que nada debe estar dentro de un **Stack**, para que se pueda sobreposicionar sobre otros widget.

Posteriormente este widget tiene que estar dentro del widget **Positioned** donde le definiremos su top, left, right o bottom y el widget que queremos posicionar como su child.

Un ejemplo seria el siguiente:

```dart
Widget build(BuildContext context) {
@override
  return Stack(
    children: [
    // purple gradiant
    Container(
      decoration: boxDecoration,
    ),
    // pickbox
    const Positioned(
      top: -100,
      left: -60,
      child: _PinkBox())
  ]);
}
```