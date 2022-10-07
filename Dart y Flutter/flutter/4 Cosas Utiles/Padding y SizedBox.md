# Padding, SizedBox y Container

El Padding, SizedBox y Container nos ayudaran a definir espacios para nuestros contenidos como si se tratara del margin y padding en css.

## Padding

El **padding** es una propiedad del widget **Padding** cual tienen que encerrar a un widget para definir el padding mismo y requiere de un valor de tipo **EdgeInsets**, entre los valores que podemos asignar esta:

* ```padding: EdgeInsets.symmetric()``` para definir el padding en el eje horizontal y vertical.
* ```padding: EdgeInsets.all()``` para padding en todos los lados
* ```padding: EdgeInsets.only()``` para definir en que lado queremos el padding.

Un ejemplo seria el siguiente:

```dart
ElevatedButton(
    child: const Padding(
    padding: EdgeInsets.symmetric(horizontal: 20, vertical: 10),
    child: Text(
        'AlertScreen',
        style: TextStyle(fontSize: 20),
        ),
    ),
    onPressed: () {
    Platform.isAndroid
        ? displayDialogAndroid(context, "Alerta")
        : displayDialogIos(context, "Alerta");
    },
),
```

## SizedBox

Sirve principalmente para dejar un espacio entre widgets.

por ejemplo: ```SizedBox(height: 10)```

## Container