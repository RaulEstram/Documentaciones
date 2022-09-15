# AppRoutes mejorando rutas.

Vamos a ver una forma de mantener las rutas de nuestra aplicación de forma ordenada.

Para esto tenemos que crear el archivo **./route/app_routes.dart** el cual tendrá una clase que nos servirá para administrar nuestras rutas de forma fácil y sencilla.

## Estructura basica

En el archivo **app_routes.dart** tendremos que crear un codigo similar al siguiente:

```dart
import 'package:flutter/material.dart';
import 'package:componentes_app/screens/screens.dart';

class AppRoute {
  static const initialRoute = "home_screen";

  static Map<String, Widget Function(BuildContext)> routes = {
    'home_screen': (BuildContext context) => const HomeScreen(),
    'listview_screen': (BuildContext context) => const ListviewScreen(),
    'card_screen': (BuildContext context) => const CardScreen(),
  };

  static Route<dynamic> onGenerateRoute(RouteSettings settings){
    return MaterialPageRoute(builder: (context) => const AlertScreen());
  }
}
```

El anterior código nos servirá para gestionar nuestras rutas de una mejor forma.

Por lo tanto, si implementamos esta clase en el archivo **main.dart** nos quedaria algo similar a lo siguiente:

```dart
import 'package:flutter/material.dart';

import 'package:componentes_app/routes/app_routes.dart';
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
      initialRoute: AppRoute.initialRoute,
      routes: AppRoute.routes,
      onGenerateRoute: (settings) =>  AppRoute.onGenerateRoute(settings),
      //onGenerateRoute: AppRoute.onGenerateRoute,
    );
  }
}
```

Podemos apreciar como las propiedades **initialRoute, routes y onGenerateRoute** del objeto **MaterialApp** quedan más limpios gracias a nuestra clase **AppRoute**.


## Mejorando clase AppRoute

En aplicaciones grandes vamos a tener muchas rutas, por lo que no es tan viable estar creando nuevos elementos para el mapa **routes**.

Para optimizar esto, crearemos una lista con todos los datos necesarios para nuestras rutas y una función que genere el mapa. 

A continuación el código:

```dart
import 'package:flutter/material.dart';
import 'package:componentes_app/models/menu_option.dart';
import 'package:componentes_app/screens/screens.dart';

class AppRoute {
  static const initialRoute = "home_screen";

  static final menuOptions = <MenuOption>[
    MenuOption(
        route: "Home",
        icon: Icons.home,
        name: "home",
        screen: const HomeScreen()),
    MenuOption(
        route: "listview",
        icon: Icons.list_rounded,
        name: "ListView",
        screen: const ListviewScreen()),
    MenuOption(
        route: "card",
        icon: Icons.sim_card_sharp,
        name: "Cards",
        screen: const CardScreen()),
    MenuOption(
        route: "alert",
        icon: Icons.warning,
        name: "Alert",
        screen: const AlertScreen())
  ];

  static Map<String, Widget Function(BuildContext)> getAppRoutes(){
     Map<String, Widget Function(BuildContext)> routes = {};
      for (final option in menuOptions) {
        routes.addAll({option.route: (BuildContext context) => option.screen});
      }
     return routes;
  }

  static Route<dynamic> onGenerateRoute(RouteSettings settings) {
    return MaterialPageRoute(builder: (context) => const AlertScreen());
  }
}
```

para este codigo tambien necesitamos el siguiente archivo (./models/menu_option.dart):

```dart
import 'package:flutter/cupertino.dart' show IconData, Widget;

class MenuOption {
  final String route;
  final IconData icon;
  final String name;
  final Widget screen;

  MenuOption(
      {required this.route,
      required this.icon,
      required this.name,
      required this.screen});
}
```

y por lo tanto nuestro archivo **main.dart** quedaria asi:

```dart
import 'package:flutter/material.dart';

import 'package:componentes_app/routes/app_routes.dart';
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
      initialRoute: AppRoute.initialRoute,
      routes: AppRoute.getAppRoutes(),
      onGenerateRoute: (settings) =>  AppRoute.onGenerateRoute(settings),
      //onGenerateRoute: AppRoute.onGenerateRoute,

    );
  }
}
```

## Ejemplo de implementacion de nueva forma de routes

A continución un código de ejemplo de como se podria utilizar esta nueva forma de getionar rutas a parte de utilizarlo para crear las rutas.


```dart
import 'package:componentes_app/routes/app_routes.dart';
import 'package:flutter/material.dart';
import '../models/menu_option.dart';

class HomeScreen extends StatelessWidget {
  const HomeScreen({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    final List<MenuOption> menuOptions = AppRoute.menuOptions;

    return Scaffold(
      appBar:
          AppBar(title: const Text("Home"), backgroundColor: Colors.pinkAccent),
      body: ListView.separated(
          itemBuilder: (context, index) {
            return ListTile(
              title: Text(menuOptions[index].name),
              leading: Icon(menuOptions[index].icon),
              trailing: const Icon(Icons.arrow_forward_ios_outlined),
              onTap: () {
                Navigator.pushNamed(context, menuOptions[index].route);
              },
            );
          },
          separatorBuilder: (context, index) => const Divider(),
          itemCount: menuOptions.length),
    );
  }
}
```