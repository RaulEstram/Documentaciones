# Futures

El tipo de dato Future es más usado de lo que parece, pero no es un primitivo ni tampoco es un objeto como las listas o mapas, no tiene una forma física.

El future son casi al 99% iguales que las promesas en JavaScript, por lo que podemos decir que un future no es más que una tarea asíncrona que se va a resolver o que se va a resolver en un futuro.

Es por esto que los Future son muy usados para cuando se hacen peticiones HTTP y en general cuando usamos API’s.

Un ejemplo seria el siguiente:

```dart
void main(List<String> args) {
  print('inicio programa');
  Future timeout = Future.delayed(Duration(seconds: 4), () => {print('4 segunndos despues')});
  print('fin programa');
}
```

la salida es:

```terminal
inicio programa
fin programa
4 segunndos despues
```

Los futures tambien tiene el metodo **then()**.

El propio método then() devuelve también un Future, por lo cual se pueden encadenar distintas llamadas then().

> **Note** mas informacion [aqui](https://rchavarria.github.io/blog/2015/01/29/operaciones-asincronas-en-dart-con-futures/)

Veamos un ejemplo de como funcionaria un **then()**:

```dart
void main(List<String> args) {

  print('inicio programa');

  // podemos especificar el tipo de dato que nos regresa
  Future<String> timeout = Future.delayed(Duration(seconds: 4), () {
    print('4 segunndos despues');
    return 'hola';
  });
  
  // las siguientes 2 lineas hacen lo mismo
  timeout.then((texto) => print(texto));
  timeout.then(print);
  
  print('fin programa');
}
```

La salida es la siguiente:

```dart
inicio programa
fin programa
4 segunndos despues
hola
hola
```

> **Note** Future.delayed(time, function)  Es un método de la clase Future que permite ejecutar una función después de 'x' cantidad de tiempo.

> **Note** Para definir el tiempo usamos la función Duration(), pueden ser horas, segundos, minutos, miliseguntos etc. [Mas información aqui](https://api.dart.dev/stable/2.17.6/dart-core/Duration-class.html)