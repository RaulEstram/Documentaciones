# BottomNavigationBar

Este widget es lo mismo que el AppBar pero para el bottom de nuestro screen.

Un ejemplo de este seria:

```dart
import 'package:flutter/material.dart';
import 'package:styles_app/themes/app_theme.dart';

class CustomBottomNavigationBar extends StatelessWidget {
  const CustomBottomNavigationBar({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return BottomNavigationBar(
      showSelectedLabels: true,
      showUnselectedLabels: false,
      backgroundColor: AppTheme.primary,
      unselectedItemColor: Colors.white38,
      selectedItemColor: const Color.fromARGB(255, 168, 47, 126),
      items: const [
        BottomNavigationBarItem(
          icon: Icon(Icons.calendar_month),
          label: "Opciones",
        ),
        BottomNavigationBarItem(
          icon: Icon(Icons.search),
          label: "Buscar",
        ),
        BottomNavigationBarItem(
          icon: Icon(Icons.info_outline),
          label: "Informacion",
        )
      ],
    );
  }
}

```

> **Note** Este tipo de Bar tiene que tener minimo 2 items.