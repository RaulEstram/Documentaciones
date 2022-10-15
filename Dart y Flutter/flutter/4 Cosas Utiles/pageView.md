# PageView

El PageView es un widget que nos permite realizar un cierto tipo de scroll sobre widgets que ocupan toda la pantalla, por lo que seria un scroll para varias "paginas".

Un ejemplo seria el siguiente:

```dart
import 'package:flutter/material.dart';

class ScrollScreen extends StatelessWidget {
  const ScrollScreen({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: PageView(
      scrollDirection: Axis.vertical,
      children: const [
        Page1(),
        Page2(),
      ],
    ));
  }
}

class Page1 extends StatelessWidget {
  const Page1({
    Key? key,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Stack(
      children: const [
        _Background(),
        _MainContent(),
      ],
    );
  }
}

/* 

    WIDGET PARA EL BACKGROUND DE LA PANTALLA

*/

class _Background extends StatelessWidget {
  const _Background({
    Key? key,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container(
        color: const Color.fromARGB(255, 53, 196, 224),
        width: double.infinity,
        height: MediaQuery.of(context).size.height,
        alignment: Alignment.topCenter,
        child: const Image(image: AssetImage("assets/scroll-1.png")));
  }
}

/*

    WIDGETS PARA EL CONTENIDO PRINCIPAL DE LA PANTALLA

*/

class _MainContent extends StatelessWidget {
  const _MainContent({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Center(
      child: Column(
        children: [
          SizedBox(
            height: MediaQuery.of(context).size.height * 0.1,
          ),
          const _CustomDegrees(),
          const _CustomDay(),
          Expanded(child: Container()),
          const _CustomDownArrow()
        ],
      ),
    );
  }
}

class _CustomDegrees extends StatelessWidget {
  const _CustomDegrees({
    Key? key,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container(
      alignment: Alignment.center,
      width: double.infinity,
      height: MediaQuery.of(context).size.height * 0.1,
      child: const Text(
        "11°",
        style: TextStyle(
          fontSize: 50,
          color: Colors.white,
          fontWeight: FontWeight.bold,
        ),
      ),
    );
  }
}

class _CustomDay extends StatelessWidget {
  const _CustomDay({
    Key? key,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container(
      alignment: Alignment.center,
      width: double.infinity,
      height: MediaQuery.of(context).size.height * 0.1,
      child: const Text(
        "Lunes",
        style: TextStyle(
          fontSize: 50,
          color: Colors.white,
          fontWeight: FontWeight.bold,
        ),
      ),
    );
  }
}

class _CustomDownArrow extends StatelessWidget {
  const _CustomDownArrow({
    Key? key,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container(
        alignment: Alignment.topCenter,
        width: double.infinity,
        height: MediaQuery.of(context).size.height * 0.1,
        child: const Icon(
          Icons.keyboard_arrow_down_rounded,
          color: Colors.white,
          size: 80,
        ));
  }
}

class Page2 extends StatelessWidget {
  const Page2({
    Key? key,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container(
        width: double.infinity,
        height: double.infinity,
        color: const Color.fromARGB(255, 53, 196, 224),
        child: Center(
          child: ElevatedButton(
            child: const Text("Entrar a la Aplicacion."),
            onPressed: () =>
                Navigator.pushNamed(context, "basic-information"),
          ),
        ));
  }
}
```