# Funcion de retorno

Las funciones también pueden devolver un valor junto con el llamado de la misma. Estas funciones se denominan funciones de retorno.

Su sintaxis básica es la siguiente:

```dart
return_type function_name(){  
   //statements  
   return value;  
}
```

> **Warning** El tipo de datos del valor devuelto debe coincidir con el tipo de devolución de la función.

Un ejemplo seria el siguiente:

```dart
void main(){
  
  String saludar() { 
    return "hola!!!"; 
  }
  print(saludar());
  
}
```
