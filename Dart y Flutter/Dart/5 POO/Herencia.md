# Herencia de clases

para la herencia de clases usaremos la palabra reservada **extends**

## Super constructor y super

El super constructor es el constructor de la clase padre.

la forma en la que llamamos al super constructor es de la siguiente manera:

```dart

ClassName(...): super();
```

por otro lado la palabra reservada super, nos ayuda a hacer una referencia de la clase padre, por lo que podremos usar los metodos del padre.

Un ejemplo de esto seria lo siguiente:

```dart
void main() {
  Empleado raul = Empleado("Raul", 22, 10000);
  print(raul.toString());
}

class Persona {
  // Propiedades
  late String _nombre;
  late int _edad;

  // getters & setters
  String get nombre => this._nombre;
  int get edad => this._edad;

  set nombre(String nombre) => this._nombre = nombre;
  set edad(int edad) => this._edad = edad;

  // constructor
  Persona(this._nombre, this._edad);

  // metodos
  @override
  String toString() {
    return "Persona: [Nombre = ${this._nombre}, Edad = ${this._edad}]";
  }
}

class Empleado extends Persona {
  // Propiedades
  late double _salario;

  // getters & setters
  double get salario => this.salario;

  set salario(double salario) => this.salario = salario;

  // constructor
  Empleado(String nombre, int edad, this._salario) : super(nombre, edad);

  // metodos
  @override
  String toString() {
    return "Empleado: [${super.toString()}, Salario = ${this._salario}]";
  }
}
```