# Entradas de Informacion.

Es probable que necesitemos que el usuario ingrese un valor desde la terminal para trabajar, es por esto que tenemos el siguiente codigo de ejemplo:

```dart
import 'dart:io';

void main() {
  print("Dijite su nombre");
  String nombre = stdin.readLineSync()!;
  print(nombre);

}
```