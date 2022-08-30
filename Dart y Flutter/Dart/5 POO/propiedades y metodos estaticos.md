# Propiedades y metodos estático

Cuando una propiedad o método es estático, se pueden acceder a estos sin necesidad de crear una instancia de clase.

Para esto utilizaremos la palabra reservada static.

un ejemplo seria:

```dart
void main(){
  Herramientas.listado.forEach((elemento) => {print(elemento)});
  Herramientas.imprimirListado();
}

class Herramientas{
  
  static const List<String> listado = ["Martillo", "Destormillador"];

  static void imprimirListado() => listado.forEach(print);
}
```