# Conceptos fundamentales de flutter

Hay algunos conceptos que existen en flutter y es por esto que es importante ver estos conceptos para familiarizarnos con flutter.

## Widgets

Un widget es una clase que puede tener argumentos posicionales y/o argumentos con nombre, de forma burda podriamos decir que son los elementos visibles de nuestra aplicacioin como botones, listas, barras, etc.

Todo en Flutter, son widgets, menos las clases que nosotros usamos para el funcionamiento de datos, de la app, etc.


## Tipos de Widgets

Existen 2 tipos de widgets (Ambos son clases abstractas) que son:

* StatelessWidget
* StatefulWidget

y como su mismo nombre lo indica, el **StatelessWidget es sin estado** y el **StatefulWidget es con estado**.

Esto quiero decir en pocas palabras que un **StatefulWidget** nos va a permitir saber el estado de si mismo, por ejemplo, si una de sus propiedades cambia, miesntras que el **StatelessWidget** no le importa saber si una propiedad cambia, practicamente no cambian.

Otra diferencia importante es que el **StatefulWidget** puede redibujarse a si mismo cuando sucede algun cambio, esto no quiere decir que un **StatelessWidget** no pueda, si puede, pero necesitara de metodos o funciones extras para realizarlo.