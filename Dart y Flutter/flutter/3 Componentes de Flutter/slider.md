# Slider, CheckBox y Switches

Estos Widgets cambian de estado por lo que sera necesario en este punto usar un StatefulWidget

## Slider

el **Slider** es una barra de progreso el cual no tiene mucho chiste, aunque se puede utilizar para algunas cosas.

veamos un ejemplo:

```dart
import 'package:flutter/material.dart';

class SliderScreen extends StatefulWidget {
  const SliderScreen({Key? key}) : super(key: key);

  @override
  State<SliderScreen> createState() => _SliderScreenState();
}

class _SliderScreenState extends State<SliderScreen> {
  double _currentValue = 50;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: const Text("Slider & Checks"),
        ),
        body: SingleChildScrollView(
          child: Column(
            children: [
              SizedBox(height: 30),
              Slider(
                value: _currentValue,
                max: 100,
                min: 0,
                divisions: 100,
                label: _currentValue.round().toString(),
                onChanged: (value) {
                  setState(() {
                    _currentValue = value;
                  });
                },
              ),
              Padding(
                padding: const EdgeInsets.all(8.0),
                child: FadeInImage(
                    fit: BoxFit.contain,
                    width: (MediaQuery.of(context).size.width / 100) *
                        _currentValue,
                    placeholder: const AssetImage("assets/loagingGif.gif"),
                    image: const NetworkImage(
                        "https://tierragamer.com/wp-content/uploads/2021/11/image_2021-11-05_162314.jpg")),
              )
            ],
          ),
        ));
  }
}
```

## Checkbox y Switches

Para los checkbox y los switches, estan las clases **Chackbox y Switch** pero estas clases son algo feas, por lo que se recomienda utilizar las clases **CheckboxListTile y SwitchListTile** que te permiten agregar un titulo haciendo que se vea mas bonito todo.

Unos ejemplos serian los siguientes codigos:

```dart

CheckboxListTile(
    title: const Text("Habilidar Slider"),
    value: _enableCheckbox,
    onChanged: (value) => setState(() {
        _enableCheckbox = value ?? true;
        })),
SwitchListTile(
    title: const Text("Habilidar Slider"),
    value: _enableCheckbox,
    onChanged: (value) => setState(() {
        _enableCheckbox = value;
        })),
```

> **Note** _enableCheckbox es una propiedad de su clase donde se guarda su valor para que se pueda redibujar la pantalla

> **Note** estos widgets al igual que varios otros, tienen el constructor con nombre llamadao **adaptive** que permite que el widget se adapte a la plataforma en la que se encuentra.


## Ejemplo completo de todo lo anterior

a continuacion un ejemplo donde usar todo lo anterior:

```dart
import 'package:flutter/material.dart';

class SliderScreen extends StatefulWidget {
  const SliderScreen({Key? key}) : super(key: key);

  @override
  State<SliderScreen> createState() => _SliderScreenState();
}

class _SliderScreenState extends State<SliderScreen> {
  double _currentValue = 50;
  bool _enableCheckbox = true;
  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: const Text("Slider & Checks"),
        ),
        body: SingleChildScrollView(
          child: Column(
            children: [
              const SizedBox(height: 30),
              Slider(
                value: _currentValue,
                max: 100,
                min: 0,
                divisions: 100,
                label: _currentValue.round().toString(),
                onChanged: _enableCheckbox
                    ? (value) {
                        setState(() {
                          _currentValue = value;
                        });
                      }
                    : null,
              ),
              CheckboxListTile(
                  title: const Text("Habilidar Slider"),
                  value: _enableCheckbox,
                  onChanged: (value) => setState(() {
                        _enableCheckbox = value ?? true;
                      })),
              SwitchListTile(
                  title: const Text("Habilidar Slider"),
                  value: _enableCheckbox,
                  onChanged: (value) => setState(() {
                        _enableCheckbox = value;
                      })),
              Padding(
                padding: const EdgeInsets.all(8.0),
                child: FadeInImage(
                    fit: BoxFit.contain,
                    width: (MediaQuery.of(context).size.width / 100) *
                        _currentValue,
                    placeholder: const AssetImage("assets/loagingGif.gif"),
                    image: const NetworkImage(
                        "https://tierragamer.com/wp-content/uploads/2021/11/image_2021-11-05_162314.jpg")),
              )
            ],
          ),
        ));
  }
}
```