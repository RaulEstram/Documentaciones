# Hola mundo

Todo programa en Dart necesita ser ejecutado en una función llamada **main()**, para esto tenemos como ejemplo el siguiente código:

```dart
main() {
  print("hola mundo");
}
```

El código anterior no está del todo bien, ya que nos dice que la función **main()** regresa un tipo de dato **dynamic**, el cual significa que puede retornar cualquier tipo de dato y por ente necesitaría un **return** a pesar de que no hay ningún error, esto lo podemos solucionar usando la palabra reservada **void** que indica que no regresa nada.

```dart
void main() {
  print("hola mundo");
}
```


[Regresar al Temario]()