# Provider y paquete HTTP.

Para realizar peticiones http a APIs, utilizaremos el paquete HTTP y tambien el Provider que nos ayuda a manejar todo esto ya que tienen la finalidad de ser el provedor de informacion.

## Configuracion de nuestros providers

Como nuestros providers van a estar conectados con toda nuestra aplicacion es normal que se encuentren en un nivel bastante alto, es por esto que en nuestro archivo **main.dart** tendremos que configurar esto.

Pero antes, tenemos que crear nuestros providers, los cuales los podemos ir creando en una carpeta llamada **providers** o **services**.

Para este ejemplo el "provider" que creamos es el siguiente:

```dart
import 'package:flutter/cupertino.dart';

class MoviesProviders extends ChangeNotifier{ 

  MoviesProviders(){
    print("MoviesProvider inicilizado");

    this.getOnDisplayMovies();
  }

  getOnDisplayMovies(){
    print("getOnDisplayMovies");
  }

}
```

> **Note** Como se puede apreciar los providers tienen que heredar de la clase **ChangeNotifier**.

Por ultimo tenemos que agregar este provider a nuestra aplicacion en el archivo **main.dart**

Nuestro codigo quedaria similar al siguiente:

```dart

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
    return MultiProvider(
      providers: [
        ChangeNotifierProvider(
          create: (context) => MoviesProviders(),
          lazy: false,
        )
      ],
      child: const MyApp(),
    );
  }
}
```

> **Note** podemos ver que la clase que estamos corriendo en la funcion **main** ya no es **MyApp** ahora es **AppState** el cual llama a MyApp como child.


## Realizar peticiones http

Para realizar peticiones podemos ir a la [documentacion](https://pub.dev/packages/http) del paquete http.

Un ejemplo de como realizar una peticion http al siguietne endpoint:

* https://api.themoviedb.org/3/movie/now_playing?api_key=7cac65f690d33a508980d5789144ab43&language=es-MX&page=1

Seria utilizando el siguiente codigo en un provider por ejemplo:

```dart
import 'dart:convert';

import 'package:flutter/cupertino.dart';
import 'package:http/http.dart' as http;

class MoviesProviders extends ChangeNotifier {
  String _apiKey = "7cac65f690d33a508980d5789144ab43";
  String _baseUrl = "api.themoviedb.org";
  String _language = "es-MX";

  MoviesProviders() {
    print("MoviesProvider inicilizado");

    this.getOnDisplayMovies();
  }

  getOnDisplayMovies() async {
    var url = Uri.https(_baseUrl, "3/movie/now_playing",
        {'api_key': _apiKey, 'language': _language, 'page': '1'});
    var response = await http.get(url);
    // print("response: ${response}");
    // print('Response status: ${response.statusCode}');
    // print('Response body: ${response.body}');
    final Map<String, dynamic> decodeData = json.decode(response.body);
   print(decodeData['results']); 
  }
}
```

> **Note** en la linea donde estamos creando un map 