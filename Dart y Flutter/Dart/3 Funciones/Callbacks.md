# Callbacks

Los Callbacks no son nada más y nada menos que funciones (ya sean normales o de flecha) que se llaman dentro de otra función.

Los Callbacks no son tan usadas, porque por lo general lo hacen mediante tareas asíncronas y los Callbacks no son tareas asíncronas, pero nos permiten poder controlar el orden de la ejecución dependiendo de nuestras necesidades.

Los Callbacks en pocas palabras son funciones que se ejecutan dentro de otra función gracias a que se pasaron como argumentos.

Un ejemplo sería el siguiente código:

```dart
void main(List<String> args) {
  obtenerUsuario(666, imprimirDatosUsuario);
}

void obtenerUsuario(int id, Function callback){
  Map<String, dynamic> usuario = {
    'id': id,
    'Nombre': 'Raul Estrada'
    };
  callback(usuario);
}

void imprimirDatosUsuario(Map<String, dynamic> mapa){
  print(mapa['Nombre'] + ' - id: ' + mapa['id'].toString());
}
```

La salida es:

```terminal
Raul Estrada - id: 666
```