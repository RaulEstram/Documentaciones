# For

El bucle for es una implementación de un bucle definido. El bucle for ejecuta el bloque de código un número específico de veces. Se puede usar para iterar sobre un conjunto fijo de valores, como una matriz.

A continuación se muestra la sintaxis del bucle for.

```dart
for (initial_count_value; termination-condition; step) { 
   //statements 
}   
```

Un ejemplo seria el siguiente:

```dart
void main() { 
   int num = 10; 
   int factorial = 1; 
   
   for( int i = num ; i >= 1; i-- ) { 
      factorial *= i ; 
   } 
   print(factorial.toString()); // 3628800
}
```