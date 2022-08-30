# For in

El bucle for...in se utiliza para recorrer las propiedades de un objeto.


A continuación se muestra la sintaxis del bucle **for in**.


```dart
for (variablename in object){  
   // statement or block to execute  
}
```

En cada iteración, se asigna una propiedad del objeto al nombre de la variable y este ciclo continúa hasta que se agotan todas las propiedades del objeto.

Un ejemplo seria el siguiente:

```dart
void main() { 
   var obj = [12,13,14]; 
   
   for (var prop in obj) { 
      print(prop); 
   } 
} 
```