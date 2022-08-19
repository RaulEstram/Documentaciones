# Async y Await

Las palabras clave **async y await** nos permite escribir código asincrónico que se parece al código síncrono. Por ejemplo, aquí hay un código que usa await para esperar el resultado de una función asincrónica:

```dart
await verificarVersion();
```

Para usar **await**, el código debe estar en una **función asíncrona**, **una función marcada como async**:

```dart
Future<String> version() async {
    String versionActual = await verificarVersion();return versionActual;
}
```

Recuerde, en este caso, el FUTURE resuelve un valor que luego puede usar. Aqui el ejemplo completo:

```dart
import 'dart:io';

void main() async {
    print('La Version Es: ${await version()}');
}

Future<String> version() async {
    String versionActual = await verificarVersion();return versionActual;
}

String verificarVersion() {
    sleep(Duration(seconds: 3));
    return 'BETA 1';
}
```