# GestureDectector

El Gesture detector es un widget que nos ayuda a poder realizar acciones cuando se hace "click" o "tap" en un widget, una de las principales usos sera para navegar entre screens.

un ejemplo seria:

```dart
GestureDetector(
    onTap: () => Navigator.pushNamed(context, "basic-information"),
    child: ...
```

