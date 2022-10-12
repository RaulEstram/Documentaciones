# Consumo de APIs de tipo GET y uso de Providers

El consumo de APIs en aplicaciones es muy importante cuando queremos realizar aplicaciones mas avanzadas, es por esto que necesitamos usar la libreria HTTP y Provider de dart, el provider nos ayudara a manejar la informacion obtenida del consumo de APIs.

En esta seccion vamos a ver como consumir una API adecuadamente y como usar el Provider.

Hay una serie de pasos que tenemos que realizar para implementar todo esto adecuadamente, y estos pasos serian los siguientes:

* Provar la API que consideramos en algun servicio como Postman o Insomnia.
* Mapear completamente la respuesta de la peticion.
* Crear el provider e implementarlo
* Utilizar el provider en diferentes clases

## Paso uno Mapear la respuesta de la peticion

Para mapear la respuesta de la peticion es necesario haber hecho pruebas con la API, para saber como funciona.

En este caso tenemos la peticion de una API de peliculas.

Lo que vamos a realizar es **Copiar la respuesta JSON** y la vamos a pegar en la pagina [**quicktype**](https://app.quicktype.io/) La cual nos permite mapear de forma facil las respuestas JSON en diferentes lenguajes de programacion.

> **Nota** se recomienta que esten activadas solamente las opciones **Put encode & decoder in Class** y **Use method names fromMap() & toMap()**, tambien le tenemos que cambiar el nombre de la clase principal desde la pagina a uno adecuado.

En este caso la pagina nos daria el siguiente codigo:

```dart
// To parse this JSON data, do
//
//     final popularMoviesResponse = popularMoviesResponseFromMap(jsonString);

import 'dart:convert';

class PopularMoviesResponse {
    PopularMoviesResponse({
        this.page,
        this.results,
        this.totalPages,
        this.totalResults,
    });

    int page;
    List<Result> results;
    int totalPages;
    int totalResults;

    factory PopularMoviesResponse.fromJson(String str) => PopularMoviesResponse.fromMap(json.decode(str));

    String toJson() => json.encode(toMap());

    factory PopularMoviesResponse.fromMap(Map<String, dynamic> json) => PopularMoviesResponse(
        page: json["page"],
        results: List<Result>.from(json["results"].map((x) => Result.fromMap(x))),
        totalPages: json["total_pages"],
        totalResults: json["total_results"],
    );

    Map<String, dynamic> toMap() => {
        "page": page,
        "results": List<dynamic>.from(results.map((x) => x.toMap())),
        "total_pages": totalPages,
        "total_results": totalResults,
    };
}

class Result {
    Result({
        this.adult,
        this.backdropPath,
        this.genreIds,
        this.id,
        this.originalLanguage,
        this.originalTitle,
        this.overview,
        this.popularity,
        this.posterPath,
        this.releaseDate,
        this.title,
        this.video,
        this.voteAverage,
        this.voteCount,
    });

    bool adult;
    String backdropPath;
    List<int> genreIds;
    int id;
    OriginalLanguage originalLanguage;
    String originalTitle;
    String overview;
    double popularity;
    String posterPath;
    DateTime releaseDate;
    String title;
    bool video;
    double voteAverage;
    int voteCount;

    factory Result.fromJson(String str) => Result.fromMap(json.decode(str));

    String toJson() => json.encode(toMap());

    factory Result.fromMap(Map<String, dynamic> json) => Result(
        adult: json["adult"],
        backdropPath: json["backdrop_path"],
        genreIds: List<int>.from(json["genre_ids"].map((x) => x)),
        id: json["id"],
        originalLanguage: originalLanguageValues.map[json["original_language"]],
        originalTitle: json["original_title"],
        overview: json["overview"],
        popularity: json["popularity"].toDouble(),
        posterPath: json["poster_path"],
        releaseDate: DateTime.parse(json["release_date"]),
        title: json["title"],
        video: json["video"],
        voteAverage: json["vote_average"].toDouble(),
        voteCount: json["vote_count"],
    );

    Map<String, dynamic> toMap() => {
        "adult": adult,
        "backdrop_path": backdropPath,
        "genre_ids": List<dynamic>.from(genreIds.map((x) => x)),
        "id": id,
        "original_language": originalLanguageValues.reverse[originalLanguage],
        "original_title": originalTitle,
        "overview": overview,
        "popularity": popularity,
        "poster_path": posterPath,
        "release_date": "${releaseDate.year.toString().padLeft(4, '0')}-${releaseDate.month.toString().padLeft(2, '0')}-${releaseDate.day.toString().padLeft(2, '0')}",
        "title": title,
        "video": video,
        "vote_average": voteAverage,
        "vote_count": voteCount,
    };
}

enum OriginalLanguage { EN, JA, FR }

final originalLanguageValues = EnumValues({
    "en": OriginalLanguage.EN,
    "fr": OriginalLanguage.FR,
    "ja": OriginalLanguage.JA
});

class EnumValues<T> {
    Map<String, T> map;
    Map<T, String> reverseMap;

    EnumValues(this.map);

    Map<T, String> get reverse {
        if (reverseMap == null) {
            reverseMap = map.map((k, v) => new MapEntry(v, k));
        }
        return reverseMap;
    }
}
```

En este caso este codigo tiene algunos fallos, ya que actualmente no soporta el **Null safety**, es por esto que le tenemos que hacer algunos cambios en el codigo, como arreglar este error, eliminar cosas, cambiar tipos de datos, eliminar metodos que no utilicemos e incluso dividir el codigo en varios archivos de ser necesario.

Nuestro codigo quedaria de la siguiente manera:

* popular_movies_response.dart

```dart
import 'dart:convert';
import 'package:app_peliculas/models/movie.dart';

class PopularMoviesResponse {
    PopularMoviesResponse({
        required this.page,
        required this.results,
        required this.totalPages,
        required this.totalResults,
    });

    int page;
    List<Movie> results;
    int totalPages;
    int totalResults;

    factory PopularMoviesResponse.fromJson(String str) => PopularMoviesResponse.fromMap(json.decode(str));

    factory PopularMoviesResponse.fromMap(Map<String, dynamic> json) => PopularMoviesResponse(
        page: json["page"],
        results: List<Movie>.from(json["results"].map((x) => Movie.fromMap(x))),
        totalPages: json["total_pages"],
        totalResults: json["total_results"],
    );

}
```

* movie.dart

```dart
import 'dart:convert';

class Movie {
  Movie({
    required this.adult,
    this.backdropPath,
    required this.genreIds,
    required this.id,
    required this.originalLanguage,
    required this.originalTitle,
    required this.overview,
    required this.popularity,
    this.posterPath,
    this.releaseDate,
    required this.title,
    required this.video,
    required this.voteAverage,
    required this.voteCount,
  });

  bool adult;
  String? backdropPath;
  List<int> genreIds;
  int id;
  String originalLanguage;
  String originalTitle;
  String overview;
  double popularity;
  String? posterPath;
  String? releaseDate;
  String title;
  bool video;
  double voteAverage;
  int voteCount;

  factory Movie.fromJson(String str) => Movie.fromMap(json.decode(str));

  factory Movie.fromMap(Map<String, dynamic> json) => Movie(
        adult:            json["adult"],
        backdropPath:     json["backdrop_path"],
        genreIds:         List<int>.from(json["genre_ids"].map((x) => x)),
        id:               json["id"],
        originalLanguage: json["original_language"],
        originalTitle:    json["original_title"],
        overview:         json["overview"],
        popularity:       json["popularity"].toDouble(),
        posterPath:       json["poster_path"],
        releaseDate:      json["release_date"],
        title:            json["title"],
        video:            json["video"],
        voteAverage:      json["vote_average"].toDouble(),
        voteCount:        json["vote_count"],
      );
  
  String getPosterImg(){
    return posterPath != null ? "https://image.tmdb.org/t/p/original$posterPath" : "https://i.stack.imgur.com/GNhxO.png";
  }
}
```

## Crear el provider e Implementarlo


### Crear el provider

Para crear el provider que va a controlar nuestro consumo de la API tenemos que realizar o basarnos en el siguiente codigo:

```dart
import 'package:app_peliculas/models/models.dart';
import 'package:flutter/cupertino.dart';
import 'package:http/http.dart' as http;

class PopularMoviesProviders extends ChangeNotifier {
  // propiedades para realizar la peticion API
  final String _apiKey = "7cac65f690d33a508980d5789144ab43";
  final String _baseUrl = "api.themoviedb.org";
  final String _language = "es-MX";

  // propiedad para guardar las peliculas en una lista
  List<Movie> popularMovies = [];

  // El constructor de nuestro provider, que se utilizara al iniciar nuestra aplicacion
  PopularMoviesProviders() {
    getPopularMovies();
  }

  // metodo que realiza la peticion a nuestra api y guarda los datos de las peliculas en nuestra lista
  // es una funcion async para poder usar el await, ya que realizamos peticiones.
  getPopularMovies() async {
    /*
    preparamos la peticion con Uri.https
    el primer argumento es la base de la api
    el segundo argumento es la extencion de la api
    el tercer argumento es un map donde tiene todos los parametros que le pasamos a la api

    El endpoint raw seria:
    https://api.themoviedb.org/3/movie/popular?api_key=7cac65f690d33a508980d5789144ab43&language=es-MX&page=1
    */
    var url = Uri.https(_baseUrl, "3/movie/popular",
        {'api_key': _apiKey, 'language': _language, 'page': '1'});
    // realizamos la peticion de tipo get
    var response = await http.get(url);
    // Creamos una instancia de la clase PopularMoviesResponse con el constructor fromJson
    // a partir del str del objeto que nos regresa la peticion
    final movies = PopularMoviesResponse.fromJson(response.body);
    // guardamos la lista de las peliculas en nuestra lista
    popularMovies = movies.results;
    // este metodo nos sirve para notificar a todos los widgets/objetos que estan escuchando
    // que algo cambio en el provider y que se redibujen los necesarios no todos
    notifyListeners();
  }
}
```


Si tuvieramos el consumo de varios endpoints nos quedaria similar a lo siguiente:

```dart
import 'package:app_peliculas/models/models.dart';
import 'package:flutter/cupertino.dart';
import 'package:http/http.dart' as http;

class MoviesProviders extends ChangeNotifier {
  // propiedades para realizar la peticion API
  final String _apiKey = "7cac65f690d33a508980d5789144ab43";
  final String _baseUrl = "api.themoviedb.org";
  final String _language = "es-MX";

  List<Movie> onDisplayMovies = [];
  List<Movie> popularMovies = [];

  MoviesProviders() {
    this.getOnDisplayMovies();
    this.getPopularMovies();
  }

  getOnDisplayMovies() async {
    var url = Uri.https(_baseUrl, "3/movie/now_playing",
        {'api_key': _apiKey, 'language': _language, 'page': '1'});
    var response = await http.get(url);
    final movies = NowPlayingResponse.fromJson(response.body);
    onDisplayMovies = movies.results;
    notifyListeners();
  }

  getPopularMovies() async {
    var url = Uri.https(_baseUrl, "3/movie/popular",
        {'api_key': _apiKey, 'language': _language, 'page': '1'});
    var response = await http.get(url);
    final movies = PopularMoviesResponse.fromJson(response.body);
    popularMovies = [...popularMovies, ...movies.results];
    notifyListeners();
  }
}
```

> **Note** Como se puede ver el codigo esta mas limio y realiza el consumo de 2 endpoints.

### Implementar el Provider

Para implementar el Provider en nuestra aplicacion tenemos que definirlo en nuestro archivo **main.dart** que es el nivel mas alto donde construimos nuestra aplicacion.

Y quedaria similar de la siguiente forma:

```dart
import 'package:app_peliculas/providers/movies_provider.dart';
import 'package:app_peliculas/routes/routes.dart';
import 'package:app_peliculas/themes/app_themes.dart';
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';

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

## Utilizar el provider en diferentes clases

Para utilizar la informacion obtenida del consumo de las APIs en nuestra aplicacion, tenemos que **agregar una linea de codigo en el metodo build**.

En este caso, la linea seria la siguiente:

```dart
final moviesProvider = Provider.of<MoviesProviders>(context);
```

> **Note** **MoviesProviders** es la clase que creamos para manejar las peticion http y que es nuestro Provider y que generalmente se encuentra en una carpeta que creamos llamada providers o services.


Un ejemplo de un Widget que utiliza o implementa el privider (y la linea de codgio anterior) seria el siguiente:

```dart
import 'package:app_peliculas/providers/movies_provider.dart';
import 'package:app_peliculas/widgets/widgets.dart';
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';

class HomeScreen extends StatelessWidget {
  const HomeScreen({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    final moviesProvider = Provider.of<MoviesProviders>(context);

    return Scaffold(
      appBar: AppBar(title: const Text("Peliculas App"), actions: [
        IconButton(
          icon: const Icon(Icons.search),
          onPressed: () {},
        )
      ]),
      body: SingleChildScrollView(
        child: Column(
          children: [
            CardsSwiper(movies: moviesProvider.onDisplayMovies),
            CardsSlider(movies: moviesProvider.popularMovies)
          ],
        ),
      ),
    );
  }
}
```

> **Note** podemos ver que la linea de codigo para acceder a la informacion del provider nos permite acceder a las propiedades y metodos del objeto que le estamos especificando, esto nos permite almacenar la informacion importante del consumo de APIs en propiedades para pasarlas como argumentos en otros widgets como es en el anterior codigo.

En el siguiente codigo podemos ver la estructura de un widget que se le pasa datos que se obtuvieron mediante el consumo de APIs.

```dart
import 'package:app_peliculas/models/movie.dart';
import 'package:flutter/material.dart';

class CardsSlider extends StatelessWidget {
  const CardsSlider({
    Key? key,
    required this.movies,
    this.title,
  }) : super(key: key);

  final List<Movie> movies;
  final String? title;

  @override
  Widget build(BuildContext context) {
    if (movies.isEmpty) {
      return const SizedBox(
        width: double.infinity,
        height: 300,
        child: Center(
          child: CircularProgressIndicator(),
        ),
      );
    }

    return SizedBox(
      width: double.infinity,
      height: 300,
      child: Column(
        children: [
          Padding(
            padding: const EdgeInsets.all(8.0),
            child: Text(
              title ?? "Populares",
              style: const TextStyle(fontSize: 25, fontWeight: FontWeight.bold),
            ),
          ),
          Expanded(
            child: ListView.builder(
              scrollDirection: Axis.horizontal,
              itemCount: movies.length,
              itemBuilder: (context, index) {
                Movie movie = movies[index];

                return _CustomCardMovieWidget(
                  url: movie.getPosterImg(),
                  title: movie.title,
                );
              },
            ),
          ),
        ],
      ),
    );
  }
}

class _CustomCardMovieWidget extends StatelessWidget {
  final String? title;
  final String url;

  const _CustomCardMovieWidget({Key? key, this.title, required this.url})
      : super(key: key);

  @override
  Widget build(BuildContext context) {
    return GestureDetector(
      onTap: () =>
          Navigator.pushNamed(context, "details", arguments: "movie-instance"),
      child: Container(
          padding: const EdgeInsets.only(bottom: 5),
          width: 150,
          child: Card(
            clipBehavior: Clip.antiAlias,
            child: Column(
              children: [
                Expanded(
                  child: FadeInImage(
                      fit: BoxFit.cover,
                      placeholder: const AssetImage("assets/loading.gif"),
                      image: NetworkImage(url)),
                ),
                if (title != null)
                  Text(
                    title!,
                    overflow: TextOverflow.ellipsis,
                    maxLines: 2,
                    textAlign: TextAlign.center,
                  )
              ],
            ),
          )),
    );
  }
}
```

## Ejemplo de uso mas complicado de consumo de APIs

* Provider file

```dart
import 'package:app_peliculas/models/models.dart';
import 'package:flutter/cupertino.dart';
import 'package:http/http.dart' as http;

class MoviesProviders extends ChangeNotifier {
  // propiedades para realizar la peticion API
  final String _apiKey = "7cac65f690d33a508980d5789144ab43";
  final String _baseUrl = "api.themoviedb.org";
  final String _language = "es-MX";

  List<Movie> onDisplayMovies = [];
  List<Movie> popularMovies = [];
  int _popularPage = 0;

  MoviesProviders() {
    getOnDisplayMovies();
    getPopularMovies();
  }

  Future<String> _getJsonData(String endpoint, [int page = 1]) async {
    var url = Uri.https(_baseUrl, "3/movie/now_playing",
        {'api_key': _apiKey, 'language': _language, 'page': '$page'});
    var response = await http.get(url);
    return response.body;
  }

  getOnDisplayMovies() async {
    final jsonData = await _getJsonData("3/movie/now_playing");
    final movies = NowPlayingResponse.fromJson(jsonData.toString());
    onDisplayMovies = movies.results;
    notifyListeners();
  }

  getPopularMovies() async {
    _popularPage++;
    print(_popularPage);
    final jsonData = await _getJsonData("3/movie/popular", _popularPage);
    final movies = PopularMoviesResponse.fromJson(jsonData.toString());
    popularMovies = [...popularMovies, ...movies.results];
    notifyListeners();
  }
}
```

* archivo donde se obtienen datos del provider

```dart
import 'package:app_peliculas/providers/movies_provider.dart';
import 'package:app_peliculas/widgets/widgets.dart';
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';

class HomeScreen extends StatelessWidget {
  const HomeScreen({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    final moviesProvider = Provider.of<MoviesProviders>(context);

    return Scaffold(
      appBar: AppBar(title: const Text("Peliculas App"), actions: [
        IconButton(
          icon: const Icon(Icons.search),
          onPressed: () {},
        )
      ]),
      body: SingleChildScrollView(
        child: Column(
          children: [
            CardsSwiper(movies: moviesProvider.onDisplayMovies),
            CardsSlider(
              movies: moviesProvider.popularMovies,
              title: "Popular",
              nextPage: () {
                moviesProvider.getPopularMovies();
              },
            )
          ],
        ),
      ),
    );
  }
}
```

* archivo donde realizamos el uso de los datos del consumo de la API.

```dart
import 'package:app_peliculas/models/movie.dart';
import 'package:flutter/material.dart';

class CardsSlider extends StatefulWidget {
  const CardsSlider({
    Key? key,
    required this.movies,
    required this.nextPage,
    this.title,
  }) : super(key: key);

  final List<Movie> movies;
  final String? title;
  final Function nextPage;

  @override
  State<CardsSlider> createState() => _CardsSliderState();
}

class _CardsSliderState extends State<CardsSlider> {
  final ScrollController scrollController = ScrollController();

  bool isLoading = false;
  @override
  void initState() {
    super.initState();

    scrollController.addListener(() {
      if (scrollController.position.pixels >=
          scrollController.position.maxScrollExtent - 500) {
        fetchMovie();
      }
    });
  }

  Future fetchMovie() async {
    if (isLoading) return;
    isLoading = true;

    setState(() {});
        await Future.delayed(const Duration(seconds: 1));


    await widget.nextPage();

    isLoading = false;

    setState(() {});

    if (scrollController.position.pixels + 100 <=
        scrollController.position.maxScrollExtent) return;
    scrollController.animateTo(scrollController.position.pixels + 120,
        duration: const Duration(seconds: 1), curve: Curves.fastOutSlowIn);
  }

  @override
  Widget build(BuildContext context) {
    if (widget.movies.isEmpty) {
      return const SizedBox(
        width: double.infinity,
        height: 300,
        child: Center(
          child: CircularProgressIndicator(),
        ),
      );
    }

    return SizedBox(
      width: double.infinity,
      height: 300,
      child: Column(
        children: [
          if (widget.title != null)
            Padding(
              padding: const EdgeInsets.all(8.0),
              child: Text(
                widget.title!,
                style:
                    const TextStyle(fontSize: 25, fontWeight: FontWeight.bold),
              ),
            ),
          Expanded(
            child: ListView.builder(
              controller: scrollController,
              scrollDirection: Axis.horizontal,
              itemCount: widget.movies.length,
              itemBuilder: (context, index) {
                Movie movie = widget.movies[index];

                return _CustomCardMovieWidget(
                  url: movie.getPosterImg(),
                  title: movie.title,
                );
              },
            ),
          ),
        ],
      ),
    );
  }
}

class _CustomCardMovieWidget extends StatelessWidget {
  final String? title;
  final String url;

  const _CustomCardMovieWidget({Key? key, this.title, required this.url})
      : super(key: key);

  @override
  Widget build(BuildContext context) {
    return GestureDetector(
      onTap: () =>
          Navigator.pushNamed(context, "details", arguments: "movie-instance"),
      child: Container(
          padding: const EdgeInsets.only(bottom: 5),
          width: 150,
          child: Card(
            clipBehavior: Clip.antiAlias,
            child: Column(
              children: [
                Expanded(
                  child: FadeInImage(
                      fit: BoxFit.cover,
                      placeholder: const AssetImage("assets/loading.gif"),
                      image: NetworkImage(url)),
                ),
                if (title != null)
                  Text(
                    title!,
                    overflow: TextOverflow.ellipsis,
                    maxLines: 2,
                    textAlign: TextAlign.center,
                  )
              ],
            ),
          )),
    );
  }
}
```