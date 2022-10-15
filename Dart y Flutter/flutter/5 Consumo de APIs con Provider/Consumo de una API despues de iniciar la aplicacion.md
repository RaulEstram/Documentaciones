# Explicacion de consumo de APIs de tipo GET despues del inicio de la aplicacion abriendo nuevas ventadas

Para esta explicacion omitiremos pasos como la crecion del provider, su implementacion o el mapeado de la respuesta de la peticion y nos enfocaremos en lo importante

## Explicacion

Cuando un widget necesita informacion que se obtenga de una api, cuando se crea al abrir una nueva ventana por ejemplo, a la creacion de ese widget le tenemos que agregar unas cosas diferentes, como son:

* **Definir el provider** que esta utilizando **en el** metodo **build**

```dart
final moviesProvider = Provider.of<MoviesProviders>(context, listen: false);
```

* **Retornar** un **FutureBuider**, este dentra 2 argumentos, **future y builder**
    * **En el future**, tenemos que definir **la funcion de nuestro provider que nos regresara** la **informacion en forma de un Future**
    * En el **builder** se le pasara una funcion con **context y snapshot** como **argumentos**, donde **snapshot** tendra la **informacion** que **nos regresara** el **future**.
        * **snapshot** tienen la propiedad hasData para saber si ya tiene la informacion, y la proiedad **data** que es donde tiene la informacion que nos regresa la funcion de **future** como tal.

```dart
@override
  Widget build(BuildContext context) {
    final moviesProvider = Provider.of<MoviesProviders>(context, listen: false);

    return FutureBuilder(
      future: moviesProvider.getMovieCast(movieId),
      builder: (context, snapshot) {
        if (!snapshot.hasData) {
          return const SizedBox(
            width: double.infinity,
            height: 180,
            child: Center(
              child: CircularProgressIndicator(),
            ),
          );
        }
        return Container(
            margin: const EdgeInsets.only(bottom: 20),
            width: double.infinity,
            height: 180,
            child: ListView.builder(
              scrollDirection: Axis.horizontal,
              itemCount: snapshot.data!.length,
              itemBuilder: (context, index) {
                return _CastCard(cast: snapshot.data![index]);
              },
            ));
      },
    );
  }
```

## Ejemplo semi completo

Un ejemplo para que veamos un poco mejor la estructura de esto serian los siguientes codigos:

* Screen que recibe unformacion consumida por una API de una pelicula en forma de argumento.

```dart
import 'package:app_peliculas/models/movie.dart';
import 'package:flutter/material.dart';

import '../widgets/widgets.dart';

class DetailScreen extends StatelessWidget {
  const DetailScreen({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    //TODO: cambiar por una instancia de movie
    final Movie movie = ModalRoute.of(context)!.settings.arguments as Movie;

    return Scaffold(
        body: CustomScrollView(
      slivers: [
        _CustomAppBarSliver(movie: movie),
        SliverList(
            delegate: SliverChildListDelegate([
          _PosterAndTitle(movie: movie),
          _Overview(movie: movie),
          CastingCards(movieId: movie.id)
        ])),
      ],
    ));
  }
}

class _CustomAppBarSliver extends StatelessWidget {
  const _CustomAppBarSliver({Key? key, required this.movie}) : super(key: key);

  final Movie movie;

  @override
  Widget build(BuildContext context) {
    return SliverAppBar(
      expandedHeight: MediaQuery.of(context).size.height / 3,
      pinned: true,
      flexibleSpace: FlexibleSpaceBar(
        background: FadeInImage(
          image: NetworkImage(movie.getBackdropPath()),
          placeholder: const AssetImage("assets/loading.gif"),
          fit: BoxFit.cover,
        ),
        centerTitle: true,
        title: Container(
          width: double.infinity,
          color: const Color.fromARGB(75, 0, 0, 0),
            child: Text(
          movie.title,
          maxLines: 2,
          textAlign: TextAlign.center,
          overflow: TextOverflow.ellipsis,
        )),
      ),
    );
  }
}

class _PosterAndTitle extends StatelessWidget {
  const _PosterAndTitle({Key? key, required this.movie}) : super(key: key);
  final Movie movie;

  @override
  Widget build(BuildContext context) {
    return Container(
      margin: const EdgeInsets.only(top: 20),
      padding: const EdgeInsets.symmetric(horizontal: 20),
      width: double.infinity,
      height: 250,
      child: Row(
        children: [
          // cartel de la pelicula
          SizedBox(
            height: 250,
            width: MediaQuery.of(context).size.width * 0.4,
            child: Padding(
              padding: const EdgeInsets.only(bottom: 5),
              child: Card(
                child: FadeInImage(
                    fit: BoxFit.cover,
                    placeholder: const AssetImage("assets/loading.gif"),
                    image: NetworkImage(movie.getPosterImg())),
              ),
            ),
          ),
          // informacion de la pelicula
          ConstrainedBox(
            constraints: BoxConstraints(
                maxWidth: MediaQuery.of(context).size.width * 0.48),
            child: Padding(
              padding: const EdgeInsets.all(8.0),
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  Text(
                    movie.title,
                    style: const TextStyle(fontSize: 20),
                    overflow: TextOverflow.ellipsis,
                    maxLines: 2,
                  ),
                  Text(
                    movie.originalTitle,
                    style: const TextStyle(fontSize: 15),
                    overflow: TextOverflow.ellipsis,
                    maxLines: 2,
                  ),
                  Row(
                    children: [
                      Text(
                        movie.voteAverage.toString(),
                        style: const TextStyle(fontSize: 10),
                        overflow: TextOverflow.ellipsis,
                        maxLines: 2,
                      ),
                      const Icon(Icons.star_outline, size: 10),
                    ],
                  ),
                ],
              ),
            ),
          )
        ],
      ),
    );
  }
}

class _Overview extends StatelessWidget {
  const _Overview({Key? key, required this.movie}) : super(key: key);
  final Movie movie;

  @override
  Widget build(BuildContext context) {
    return Container(
      padding: const EdgeInsets.symmetric(horizontal: 20, vertical: 10),
      child: Text(
        movie.overview,
        textAlign: TextAlign.justify,
      ),
    );
  }
}
```

* Widgets para presentar la informacion del cast de una pelicula

```dart
import 'package:app_peliculas/models/credits_response.dart';
import 'package:app_peliculas/providers/movies_provider.dart';
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';

class CastingCards extends StatelessWidget {
  const CastingCards({Key? key, required this.movieId}) : super(key: key);

  final int movieId;

  @override
  Widget build(BuildContext context) {
    final moviesProvider = Provider.of<MoviesProviders>(context, listen: false);

    return FutureBuilder(
      future: moviesProvider.getMovieCast(movieId),
      builder: (context, snapshot) {
        if (!snapshot.hasData) {
          return const SizedBox(
            width: double.infinity,
            height: 180,
            child: Center(
              child: CircularProgressIndicator(),
            ),
          );
        }
        return Container(
            margin: const EdgeInsets.only(bottom: 20),
            width: double.infinity,
            height: 180,
            child: ListView.builder(
              scrollDirection: Axis.horizontal,
              itemCount: snapshot.data!.length,
              itemBuilder: (context, index) {
                return _CastCard(cast: snapshot.data![index]);
              },
            ));
      },
    );
  }
}

class _CastCard extends StatelessWidget {
  const _CastCard({Key? key, required this.cast}) : super(key: key);

  final Cast cast;

  @override
  Widget build(BuildContext context) {
    return Container(
      margin: const EdgeInsets.symmetric(horizontal: 10),
      padding: const EdgeInsets.only(bottom: 5),
      width: 100,
      height: 200,
      child: Column(
        children: [
          Expanded(
            child: Card(
              child: FadeInImage(
                placeholder: const AssetImage("assets/loading.gif"),
                image: NetworkImage(cast.getProfileImg()),
                fit: BoxFit.cover,
              ),
            ),
          ),
          Text(
            cast.name,
            style: const TextStyle(fontSize: 12),
            textAlign: TextAlign.center,
            maxLines: 2,
            overflow: TextOverflow.ellipsis,
          ),
        ],
      ),
    );
  }
}
```