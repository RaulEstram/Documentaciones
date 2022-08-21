# catchError

**catchError** es para cuando estemos trabajando con **Futures**, lo que hace es manejar los posibles **errores** que podamos llevar a tener un **then()**.

Un ejemplo de uso de catchError es el siguiente código:

```dart
void main(List<String> args) {
  Future<String> timeout = Future.delayed(Duration(seconds: 3), () {
    if (1==1) {
      throw "fallo esta madre";
    }
    return "Hola";
  });
  
  timeout.then((value) => print(value)).catchError((error) => print(error));
}
```

> **Note** Para arrojar errores usamos la palabra reservada **throw** seguido del mensaje del error.