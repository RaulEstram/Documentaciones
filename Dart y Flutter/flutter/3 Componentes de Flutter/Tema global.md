# Tema Global

Al igual que las rutas, nuestros temas los podemos tener en un archivo aparte para mejor configuracion y codigo mas limpio. un ejemplo del archivo que podemos crear seria el siguiente:

```dart
import 'package:flutter/material.dart';

class AppTheme {
  
  static const Color primary = Colors.pink;
  static const Color second = Color(0xFF283593);

  static final ThemeData lightTheme = ThemeData.light().copyWith(
    primaryColor: primary,
    appBarTheme: const AppBarTheme(
      color: primary,
      elevation: 0
    )
  );

  static final ThemeData darkTheme = ThemeData.light().copyWith(
    primaryColor: primary,
    appBarTheme: const AppBarTheme(
      color: primary,
      elevation: 0
    )
  );
}
```

por lo tanto quedaria de la siguiente manera en el main.dart


```dart
import 'package:componentes_app/theme/app_theme.dart';
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
      onGenerateRoute: (settings) => AppRoute.onGenerateRoute(settings),
      //onGenerateRoute: AppRoute.onGenerateRoute,
      theme: AppTheme.lightTheme,
    );
  } 
}
```