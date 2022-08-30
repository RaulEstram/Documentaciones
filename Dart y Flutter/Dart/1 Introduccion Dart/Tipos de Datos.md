# Tipos de datos

Dart es un lenguaje de programación en donde tienes que definir el tipo de dato de cada variable, o de lo que regresa una función, en este sentido es similar a Java.

En Dart encontraremos los siguientes tipos de datos:

* Numeros
* Strings

## Creacion de variables

Para crear variables tenemos que utilizar la siguiente sintaxis:

```dart
{tipo de dato} {nombre de la variable} = {valor de la variable};
```

o tambien podemo utilizar la siguiente sintaxis:

```dart
{tipo de dato} {nombre de la variable};
```

Por otra parte tambien podemos definir variables de tipo String y booleanos sin definir el tipo de dato usando la siguiente sintaxis:

```dart
{nombre de la variabel} = {valor de la variable}
```


## Numeros

Los numeros en Dart se pueden clasificar en 2 tipos de datos que son:

* int = para numeros enteros
* double = para numeros con punto decimal

veamos un ejemplo de como se definen estos tipos de datos:

```dart
void main() {
  int empleados = 10;
  double salario = 15698.54;

  print('$empleados - $salario');
}
```

## String

Los Strings son para almacenar texto y unos ejemplos de como lo podemos definir son los siguientes:

```dart
void main() {
  String nombre = "Raúl";
  apellido = 'Estrada';

  print('$nombre $apellido');
}

```

> **Note** podemos definir los Strings entre comillas dobles o entre comillas simples


## Booleanos

Los tipos de datos booleanos soportan los valores **true, false y null**.

veamos un ejemplo de como se define y se usan los booleanos:

```dart
void main() {
  bool isActive = true;
  
  if(!isActive){
    print("Está activo.");
  } else {
    print("Está inactivo.");
  }
}
```

> **Note** el signo de "!" nos indica negacion al igual que en varios lenguajes de programacion por lo que imprimiria "Esta inactivo"


A partir de la versión 2.12 de Dart, se agregó una nueva función para las variables cuyo valor sea **null** llamada **Null Safety**.

Esta función significa que si definimos que una variable no puede tener valores nulos, nunca va a guardar un valor nulo.

Por otro lado, si especificamos que una variable puede tener un valor nulo, entonces Dart se va a encargar de ayudarnos a indicar cuando nuestro código es inseguro o es probable que tenga errores.

Para definir que una variable puede tener valores nulos, utilizaremos el signo de cierre de pregunta al final de la definición del tipo de dato.

veamos un ejemplo:

```dart
void main() {
  bool? isNull = null; // Puede ser nulo
  bool isActive = true; // No puede ser nulo
  
  if(isNull == null){
    print("Es null.");
  } else {
    print("No es null.");
  }
}
```

## Listas o List

Las listas o **List** son una colección de datos que tienen algún tipo de dato en común.

veamos un ejemplo de como se definen:

```dart
void main() {
  // Definimos la listta
  List numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  
  // agregar un valor a la lista
  numeros.add(11);
  
  // obtener un valor de una lista
  print(numeros[0]); // 1

  // agregar otro tipo de dato a la lista
  numeros.add("Hola mundo");
  
  // imprimimos la lista
  print(numeros); // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, Hola mundo]
}
```

A pesar de que el anterior código es funcional, no es lo más adecuado, ya que la lista es de tipo **dynamic**, esto quiere decir que va a aceptar diferentes tipos de datos.

Esto no es malo o erróneo, pero se recomienda que se trabaje con un solo tipo de dato, es por ello que utilizaremos "<{tipo de dato}>" para definir que con que tipo de datos trabajara la lista.

veamos un ejemplo:

```dart
void main() {
  List<int> numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  numeros.add(11); 
  print( numeros ); 
  
  final masNumeros = List.generate(100, (int index) => index );
  print(masNumeros);
}
```

## Map

Los tipos de datos **map** también se le conocen como mapas u objetos literales y son similares a los diccionarios en Python.

la sintaxis que los map es la siguiente:

```dart
Map[<{tipo de dato de la llave}, {tipo de dato del valor}>] {nombre del map} = {
  {key}: {value},
  {key2}: {value2}
};
```

veamos un ejemplo de uso de map:

```dart
void main() {
  // ejemplo 1, map<dynamic, dynamic>
  Map persona = {
    'nombre': 'Raúl',
    'apellido': 'Estrada',
    1 : 'uno',
  }; 
  print(persona['nombre'] + " " + persona['apellido']);

  
  Map<String, dynamic> persona2 = <String, dynamic>{};
  persona2.addAll({'nombre': 'paco', 'apellido': 'gerte'});
  print(persona2);
}
```


[Regresar al Temario]()