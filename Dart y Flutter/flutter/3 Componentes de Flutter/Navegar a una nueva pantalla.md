# Navegar a una nueva plantilla

Hay 2 formas para navegar entre pantallas, una más completa pero complicada y una fácil y rápida.

## Forma larga pero mas completa

```dart
onTap: () {
    final route = MaterialPageRoute(builder: (context) => const ListviewScreen());
    Navigator.push(context, route);
},
```

Tambien tenemos **Navigator.pushReplacement(context, route)** donde pasamos a una nueva pantalla pero "destruye" la ruta anterior, por lo que no puedes regresarte, esto es util si tenemos algun screen para el login y despues de que se loguean, ya no queremos que se regresen las personas

> **Note** esta forma es util si queremo spersonalizar las transisiones y todas esas cosas

## Forma rapida

Esta forma es la más rápida para transicional a otro screen, y para ello utiliza las rutas que podemos definir en el objeto MaterialApp de nuestra aplicación.

```dart
onTap: () {
    Navigator.pushNamed(context, "listview_screen");
},
```

Como se puede ver la sintaxis es muy basica ya que es:

```dart
Navigator.pushNamed(context, {Una ruta de nuestra clase Material App});
```

Tammbien tenemos **Navigator.pushReplacementNamed(context, "route");** donde pasamos a una nueva pantalla pero "destruye" la ruta anterior, por lo que no puedes regresarte, esto es util si tenemos algun screen para el login y despues de que se loguean, ya no queremos que se regresen las personas

## Redirección de una ruta errónea.

Es posible que mientras estamos programando y creando las navegaciones entre diferentes screens lleguemos a poner una ruta errónea. En estos casos podemos redireccionar la aplicación a una ruta por defecto.

Para la redirección usaremos la propiedad **onGenerateRoute** de nuestro objeto **MarerialApp**.

A esta propiedad le tendremos que pasar una función que regrese un **MaterialPageRoute**.

A continuación un ejemplo:

```dart
import 'package:flutter/material.dart';

import 'package:componentes_app/screens/screens.dart';

void main() => runApp(const MyApp());

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Material App',
      //home: const ListviewScreen(),
      initialRoute: 'home_screen',
      routes: {
        'home_screen': (BuildContext context) => const HomeScreen(),
        'listview_screen': (BuildContext context) => const ListviewScreen(),
        'card_screen': (BuildContext context) => const CardScreen(),
      },
      onGenerateRoute: (settings) {
        return MaterialPageRoute(
          builder: (context) => const AlertScreen(),
        );
      },
    );
  }
}

```