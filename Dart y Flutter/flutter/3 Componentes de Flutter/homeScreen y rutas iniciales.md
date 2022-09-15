# HomeScreen y rutas Iniciales

Una forma para ir definiendo las rutas de nuestra aplicacion seria usando la propiedad **routes y initialRoute** de nuestra clase **MaterialApp**, en donde:

* ```routes``` lo utilizamos para definir las rutas de nuestra aplicacion
* ```initialRoute``` lo utilizamos para definir la ruta inicial de nuestra aplicación.

Un ejemplo seria:

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
        initialRoute: 'listview_screen',
        routes: {
          'home_screen'     : (BuildContext context) => const HomeScreen(), 
          'listview_screen' : (BuildContext context) => const ListviewScreen(),
          'alert_screen'    : (BuildContext context) => const AlertScreen(),
        });
  }
}
```

En el anterior código podemos apreciar que usamos la propiedad **route** donde le pasamos un map con la ruta (en string) como key y el Screen como value

> **Nota** De esta forma podemos evitar el uso de la propiedad home.