# Final, const y late

**final** es una palabra reservada de Dart que nos indica que una variable no va a cambiar su valor.

Veamos un ejemplo de una variable definida como **final**.

```dart
void main() {
  final String nombre = "Raúl";
  String apellido = 'Estrada';
  
  // template string
  print('$nombre $apellido');
}
```

> **Warning** Si una variable se define como Final, y se intenta cambiar su valor, se producirá un Error.

**const** por otro lado significa que el valor de una variable nunca va a cambiar en tiempo de compilacion.

Veamos un ejemplo de una variable definida como **const**.


```dart
void main() {
  const String nombre = "Raúl";
  String apellido = 'Estrada';
  
  // template string
  print('$nombre $apellido');
}
```

## Diferencia entre const y final

Las variables de tipo **const y final** sólo pueden ser declaradas al mismo tiempo de ser creadas, su diferencia mayor es que final es inicializada al momento de usarse, mientras const al momento de escribirse.

**final** se pueden instanciar en tiempo de ejecucion y los **const** NO, gracias a esto podemos hacer lo siguiente:

```dart
final date = new DateTime.now();
```

pero no podemos hacer lo siguiente:

```dart
const date = new DateTime.now();
```

En conclusion: 

* Const:  El valor  debe conocerse en tiempo de compilación ,no se puede cambiar después de inicializado.
* Final: El valor debe conocerse en tiempo de ejecución ```final birthday = getBirthDateFromDB()``` , pero no se puede cambiar después de inicializado.

## Late

**lete** nos sirve para decirle a Dart que mas tarde se le dará un valor a la variable.

```dart
void main() {
  late final double numero;
  numero = 10.0;
  print(numero);
}
```

[Regresar al Temario]()