# Enumeraciones

Las enumeraciones nos pueden facilitar la lectura de nuestro código cuando necesitamos cierto tipo de datos o de valores.


Una enumeración se utiliza para definir valores constantes con nombre. Un tipo enumerado se declara mediante la palabra clave enum.

La sintaxis es la siguiente:

```dart
enum enum_name {  
   enumeration list 
}
```

Un ejemplo es el siguiente:

```dart
void main(List<String> args) {
  // una enumeracion es como una funcion
    
  Audio volumenAudio = Audio.bajo;
  
  switch (volumenAudio) {
    case Audio.bajo: print("Volumen Bajo"); break;
    case Audio.medio: print("Volumen Medio"); break;
    case Audio.alto: print("Volumen Alto"); break;
  }
}

enum Audio{
  bajo,
  medio,
  alto
}
```