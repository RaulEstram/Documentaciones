# BottomNavigationBar

Para crear un **BottomNavigationBar** necesitamos realizar varios pasos para que este sea funcional como es:

* crear un gestor de estado o tambien conocido como un Provider
* Implementar el Provider
* crear el widget de nuestro **BottomNavigationBar**
* Implementarlo

## Crear un provider

Como simplemente vamos a gestionar el item del **BottomNavigationBar** que esta seleccionado tenemos que crear un **Provider** basico, en este caso seria el siguiente:

* provider/menu_prodiver.dart

```dart
import 'package:flutter/material.dart';

class BottomMenuProvider extends ChangeNotifier {
  int _selectedMenuOpt = 1;

  int get selectedMenuOpt => _selectedMenuOpt;

  set selectedMenuOpt(int option) {
    _selectedMenuOpt = option;
    notifyListeners();
  }
}
```

## Implementar el provider

Para implementarlo tenemos que crear una nueva clase en nuestro archivo **main.dart**, el cual quedaria de la siguiente manera:

```dart
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';
import 'package:qr_app/provider/menu_prodiver.dart';
import 'package:qr_app/routes/routes.dart';
import 'package:qr_app/theme/app_theme.dart';

void main() => runApp(const AppState());

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Material App',
      initialRoute: AppRoute.initialRoute,
      routes: AppRoute.getAppRoutes(),
      onGenerateRoute: (settings) => AppRoute.onGenerateRoute(settings),
      theme: AppTheme.lightTheme,
    );
  }
}

class AppState extends StatelessWidget {
  const AppState({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MultiProvider(providers: [
      ChangeNotifierProvider(
        create: (context) => BottomMenuProvider(),
        lazy: false,
      )
    ],
    child: const MyApp(),
    
    );
  }
}
```

## Crear nuestro BottomNavigationBar

Para nuestro BottomNavigationBar, tenemos que conectarlo con nuestro Provider para definir el item por defecto que estara seleccionado y que cuando cambie se cambie el item seleccionado.

Para cambiar el item seleccionado es importante usar la propiedad **onTap** para realizar el cambio en el provider del estado de la opcion seleccionada.

Un ejemplo de nuestro BottomNavigationBar seria el siguiente:

```dart
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';
import 'package:qr_app/provider/menu_prodiver.dart';

class CustomNavigationBar extends StatelessWidget {
  const CustomNavigationBar({
    Key? key,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {

    final menuProvider = Provider.of<BottomMenuProvider>(context);

    final currentIndex = menuProvider.selectedMenuOpt;

    return BottomNavigationBar(
      onTap: (value) {
        menuProvider.selectedMenuOpt = value;
      },
      currentIndex: currentIndex,
      items: const [
        BottomNavigationBarItem(
          icon: Icon(Icons.map_outlined),
          label: "Mapa",
        ),
        BottomNavigationBarItem(
          icon: Icon(Icons.directions),
          label: "Direcciones",
        ),
      ],
    );
  }
}
```

## Implementacion del BottomNavigationBar

Para implementarlo se podria decir que lo mas facil seria que cambie el contenido de un screen, por lo que utilizariamos un widget que obtenga el valor de la opcion seleccionada de nuestro provider y regrese mediante un switch el contenido que se quiere mostrar.

Un ejemplo seria el siguiente:

```dart
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';
import 'package:qr_app/provider/menu_prodiver.dart';
import 'package:qr_app/screens/mapas_screens.dart';
import 'package:qr_app/screens/screens.dart';

import '../widgets/widgets.dart';

class HomeScreen extends StatelessWidget {
  const HomeScreen({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("hola"),
      ),
      body: const _HomePageBody(),
      bottomNavigationBar: const CustomNavigationBar(),
      floatingActionButton: const CustomFloatingButtomNavigationBar(),
      floatingActionButtonLocation: FloatingActionButtonLocation.centerDocked,
    );
  }
}

class _HomePageBody extends StatelessWidget {
  const _HomePageBody({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    // obtener el selected menu opt
    final menuProvider = Provider.of<BottomMenuProvider>(context);

    // cambiar para que cambie la vista
    final currentIndex = menuProvider.selectedMenuOpt;

    switch (currentIndex) {
      case 0:
        return const MapsScreen();
      case 1:
        return const DireccionesScreen();
      default:
        return const MapsScreen();
    }
  }
}

```