# Slivers

Los Slivers son un conjunto de Widgets que nos permite que nuestras aplicaciones tengan sienta movilidad, por ejemplo que el AppBar se oculte cuando estemos bajando por el contenido de nuestro screen

para utilizarlos tendemos que usar un **ScrollCustom** que en lugar de pasarle un child o children le pasaremos un **slivers** donde contendra todos los **widgets de tipo sliver**, pero como la gran mayoria de nuestros widgets no son de este tipo, tenemos el objeto **SliverList(delegate: SliverChildListDelegate([]))** el cual le vamos a pasar todos nuestros widgets que no son de tipo sliver, para que podamos utilizarlos.

Un ejemplo seria el siguiente:

```dart
import 'package:flutter/material.dart';

import '../widgets/widgets.dart';

class DetailScreen extends StatelessWidget {
  const DetailScreen({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    //TODO: cambiar por una instancia de movie
    final String movie =
        ModalRoute.of(context)?.settings.arguments.toString() ?? 'no-movie';

    return Scaffold(
        body: CustomScrollView(
      slivers: [
        _CustomAppBarSliver(title: movie),
        SliverList(
            delegate: SliverChildListDelegate([
          const _PosterAndTitle(),
          const _Overview(),
          const CastingCards()
        ])),
      ],
    ));
  }
}

class _CustomAppBarSliver extends StatelessWidget {
  final String? title;

  const _CustomAppBarSliver({Key? key, required this.title}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return SliverAppBar(
      expandedHeight: MediaQuery.of(context).size.height / 2,
      pinned: true,
      flexibleSpace: FlexibleSpaceBar(
        background: const FadeInImage(
          image: AssetImage("assets/loading.gif"),
          placeholder: AssetImage("assets/loading.gif"),
        ),
        centerTitle: true,
        title: Text(title ?? "No Found Movie"),
      ),
    );
  }
}

class _PosterAndTitle extends StatelessWidget {
  const _PosterAndTitle({Key? key}) : super(key: key);

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
            child: const Padding(
              padding: EdgeInsets.only(bottom: 5),
              child: Card(
                child: FadeInImage(
                    fit: BoxFit.cover,
                    placeholder: AssetImage("assets/loading.gif"),
                    image: AssetImage("assets/loading.gif")),
              ),
            ),
          ),
          // informacion de la pelicula
          Padding(
            padding: const EdgeInsets.all(8.0),
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.start,
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                const Text(
                  "movie.title",
                  style: TextStyle(fontSize: 20),
                  overflow: TextOverflow.ellipsis,
                ),
                const Text(
                  "movie.original.Title",
                  style: TextStyle(fontSize: 15),
                  overflow: TextOverflow.ellipsis,
                ),
                Row(
                  children: const [
                    Text(
                      "movie.voteAverage",
                      style: TextStyle(fontSize: 10),
                      overflow: TextOverflow.ellipsis,
                    ),
                    Icon(Icons.star_outline, size: 10),
                  ],
                ),
              ],
            ),
          )
        ],
      ),
    );
  }
}

class _Overview extends StatelessWidget {
  const _Overview({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container(
      padding: const EdgeInsets.symmetric(horizontal: 20, vertical: 10),
      child: const Text(
        "Ea anim Lorem officia eiusmod fugiat non ullamco dolor nisi eiusmod laboris voluptate consectetur. Sint nostrud deserunt dolor eiusmod enim sint. Ad sint laboris consectetur velit anim commodo laborum nisi officia fugiat. Sit nisi reprehenderit culpa pariatur irure amet voluptate reprehenderit eiusmod dolore labore ullamco qui.",
        textAlign: TextAlign.justify,
      ),
    );
  }
}
```