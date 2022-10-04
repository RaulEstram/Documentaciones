# Creacion y centralizacion de Widgets personalizados

Para la centralizacion de los Widgets personalizados **crearemos un directorio llamado widgets** en donde iremos dejando todos los archivos de los Widgets personalizados.

## creacion de widgets personalizados

Para crear un widget personalizado tenemos que extraer la logica de algo que queramos y crear una clase en base a eso.

Dicha clase tiene que ser un widget por lo que tiene que heredar de la clase **StatulessWidget o StatusfulWidget**.

> **Note** **Podemos extraer la logica de un Widget con Ctrl + . -> Extract Widget** para que nos cree una clase con la logica de un widget

Un ejemplo seria:

```dart
import 'package:componentes_app/theme/app_theme.dart';
import 'package:flutter/material.dart';

class CustomCardType1 extends StatelessWidget {
  final String titulo;
  final String subtitulo;
  final IconData icono;

  const CustomCardType1({
    Key? key,
    required this.titulo,
    required this.subtitulo,
    required this.icono,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Card(
      child: Column(
        children: [
          ListTile(
            leading: Icon(
              icono,
              color: AppTheme.second,
            ),
            title: Text(titulo),
            subtitle: Text(subtitulo),
          ),
          Padding(
            padding: const EdgeInsets.only(right: 5),
            child: Row(
              mainAxisAlignment: MainAxisAlignment.end,
              children: [
                TextButton(onPressed: () {}, child: const Text("Cancelar")),
                TextButton(onPressed: () {}, child: const Text("Aceptar")),
              ],
            ),
          )
        ],
      ),
    );
  }
}
```