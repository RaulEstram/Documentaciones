# Creacion de Clases

Las clases van afuera de la función main y se recomienda que tenga la siguiente estructura:

```dart

class NombreClase{
  // campos o propiedades
  
  // Get's an Set's
  
  // constructores
  
  // metodos
}
```

## Propiedades publicas y privadas.

En nuestras clases tendremos propiedades privadas y públicas (encapsulamiento).

La diferencia reside en que una propiedad privada solo se puede usar en el scope o en el contexto de la clase.

Para definir que una propiedad es privada, usaremos un guion bajo "_" al principio de su nombre, si no lo tienen se considera que es publica.

Veamos un ejemplo:

```dart

class Persona{
  // campos o propiedades
  String? nombre;
  int? _edad;
  String _genero;
  // Get's an Set's
  
  // constructores
  
  // metodos
}
```

## Getters & Setters

Nos sirven para darle un valor a una propiedad privada o para obtener su valor.

Veamos un ejemplo:

```dart
void main(){
  
  
}


class Persona{
  // campos o propiedades
  String? nombre;
  int? _edad;
  String? _genero;
  
  // Get's an Set's
  
  // get normal
  int? get edad{
    return this._edad;
  }
  
  // get con arrow function o lambda
  String? get genero => this._genero;
  
  // set normal
  
  set edad(int? edad){
    this._edad = edad;
  }
  
  // set con arrow function o lambda
  
  set genero (String? genero) => this._genero = genero;
  
  // constructores
  
  
  // metodos
}
```

