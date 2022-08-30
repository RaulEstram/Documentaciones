# Constructores

En dart hay diferentes tipos de constructores como son:

* constructores basicos
* constructores con nombre
* constructores constantes
* constructores factory

## Constructores basicos

los constructores basicos tendran la siguiente sintaxis

```dart
class NameClass{
    NameClass(){

    }
}
```

un ejemplo seria el siguiente codigo:

```dart
class Rectangulo{
  late double ancho;
  late double altura;
  
  Rectangulo(double ancho, double altura){
    this.ancho = ancho;
    this.altura = altura;
  }
  
  @override
  String toString(){
    return "Rectangulo: [Altura: ${this.altura}, Ancho: ${this.ancho}]";
  }
}
```

otro ejemplo seria:

```dart
class Rectangulo{
  late double ancho;
  late double altura;
  
  Rectangulo(this.ancho, this.altura);
  
  @override
  String toString(){
    return "Rectangulo: [Altura: ${this.altura}, Ancho: ${this.ancho}]";
  }
}
```

> **Note** También hay que mencionar que podemos hacer que los constructores tengan parámetros opcionales posicionales o no posicionales


## Constructores con nombre

Para realzar estos constructores se llama a la clase seguida de un punto y el sub nombre o nombre de la clase y de la misma manera que los constructores normales, agregamos sus parámetros.Los constructores con nombre se utilizan en flutter, y estos constructores son útiles para crear varios tipos de constructores con enfoques en algo en especial.

Un ejemplo seria el siguiente:

```dart
void main(){
  Persona p = Persona.raul(22);
  print(p.toString());
}


class Persona{
  late int edad;
  late String nombre;
  
  Persona(this.edad, this.nombre);
  
  Persona.persona40(String nombre){
    this.nombre = nombre;
    this.edad = 40;
  }
  
  Persona.raul(this.edad){
    this.nombre = "Raul";
  }
  
  @override
  String toString(){
    return "Persona: [Nombre: ${this.nombre}, Edad: ${this.edad}]";
  }
}
```

## Constructores Constantes


Cuando definimos que un constructor es constante y creamos instancias de clase como constantes que tienen los mismos datos, lo que hacemos es que esas instancias apunten al mismo espacio de memoria.


```dart
void main(){
  Persona p1 = Persona(22, "");
  Persona p2 = Persona(22, "");
  print(p1==p2); // false
  
  Persona p3 = const Persona.raul(22);
  Persona p4 = const Persona.raul(22);
  print(p3==p4); // true
  
  const Persona p5 = Persona.raul(22);
  const Persona p6 = Persona.raul(22);
  print(p5==p6); // true
  
}


class Persona{
  final int edad;
  final String nombre;
  
  const Persona(this.edad, this.nombre);
  
  const Persona.raul(this.edad): this.nombre = "Raul";
  
  Persona.persona30(this.nombre): this.edad = 30;
  
  
  @override
  String toString(){
    return "Persona: [Nombre: ${this.nombre}, Edad: ${this.edad}]";
  }
}
```

## Constructores Factory

El Constructor factory puede ser utilizado para realizar algún tipo de procedimiento o cálculo para determinar que constructor de mi clase se adapta mejor, el Constructor factory regresa una instancia de clase.

```dart
class Rectangulo{
  
  late double base;
  late double altura;
  late String tipo;
  late double area;
  late double perimetro;
  
  factory Rectangulo(double base, double altura){
    if(base == altura){
      return Rectangulo.cuadrado(base);
    }else{
      return Rectangulo.rectangulo(base, altura);
    }
  }
  
  Rectangulo.cuadrado(double base){
    this.base = base;
    this.altura = base;
    this.area = base * base;
    this.perimetro = 4 * base;;
    this.tipo = "Cuadrado";
  }
  
  Rectangulo.rectangulo(double base, double altura){
    this.base = base;
    this.altura = altura;
    this.area = base * altura;
    this.perimetro = (2 * base) + (2 * altura);
    this.tipo = "Rectangulo";
  }
  
  @override
  String toString(){
    return "";
  }
}
```
