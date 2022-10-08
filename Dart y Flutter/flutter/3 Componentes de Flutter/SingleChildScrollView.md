# SingleChildScrollView

el **SingleChildScrollView** Este widget es útil cuando se tiene un widget muy grande y se quiere asegurar de que se pueda realizar un scroll, por ejemplo si tenemos un formulario.


Un ejemplo seria el siguiente:

```dart
import 'package:flutter/material.dart';

class InputsScreen extends StatelessWidget {
  const InputsScreen({Key? key}) : super(key: key);
  
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("Diferentes tipos de Inputs"),),
      body: SingleChildScrollView(
        child: Padding(
          padding: const EdgeInsets.symmetric(horizontal: 20, vertical: 10),
          child: Column(
            children: [
              TextFormField()
            ],
          )
        ),
      )
    );
  }
}
```