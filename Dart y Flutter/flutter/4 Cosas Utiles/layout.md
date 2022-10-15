# Tipos de Layout

Tenemos diferentes tipos de layout para posicionar diferentes items, entre los mas relevantes tenemos:

* [GridView](https://api.flutter.dev/flutter/widgets/GridView-class.html) Para posicionar items/widgets en forma de "caja".
* [Stack](https://api.flutter.dev/flutter/widgets/Stack-class.html) Para posicionar items encima de otros widgets

> **Note** el GridView tiene varios constructores que nos pueden ayudar como es el ListView

## Ejemplo de GridView:


```dart
return GridView.builder(
    padding: const EdgeInsets.symmetric(horizontal: 10),
    gridDelegate: const SliverGridDelegateWithFixedCrossAxisCount(
        crossAxisCount: 2,
    ),
    itemCount: optionList.length,
    physics: const BouncingScrollPhysics(),
    itemBuilder: (context, index) {
        return optionList[index];
    },
);
```