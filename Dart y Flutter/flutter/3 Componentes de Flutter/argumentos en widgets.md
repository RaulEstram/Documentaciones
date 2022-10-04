# Argumentos en los Widgets.

Para agregar argumentos a nuestros widgets es necesario definirlos hasta arriba de la clase.

Después los agregamos al constructor, ya sean requeridos o no.

Y por último estaría usarlos dentro de la lógica de la construcción de nuestro widget. Donde podemos utilizar sentencias como el if para que nuestro widget tenga ciertas cosas dependiendo de si se le pasa un argumento o no.

un ejemplo de todo lo anterior seria lo siguiente:

```dart
import 'package:componentes_app/theme/app_theme.dart';
import 'package:flutter/material.dart';

class CustomCardType2 extends StatelessWidget {
  final String imageUrl;
  final String? title;

  const CustomCardType2({Key? key, required this.imageUrl, this.title})
      : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Card(
      shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(15)),
      elevation: 10,
      shadowColor: AppTheme.second.withOpacity(0.5),
      clipBehavior: Clip.antiAlias,
      child: Column(
        children: [
          FadeInImage(
            placeholder: const AssetImage("assets/loagingGif.gif"),
            image: NetworkImage(imageUrl),
            width: double.infinity,
            height: 230,
            fit: BoxFit.cover,
            fadeInDuration: const Duration(milliseconds: 300),
          ),
          if (title != null)
            Container(
              alignment: AlignmentDirectional.center,
              padding: const EdgeInsets.only(top: 10, bottom: 10),
              child: Text(title!),
            )
        ],
      ),
    );
  }
}
```