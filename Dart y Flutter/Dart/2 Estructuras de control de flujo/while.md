# while

El bucle while ejecuta las instrucciones cada vez que la condición especificada se evalúa como verdadera. En otras palabras, el bucle evalúa la condición antes de ejecutar el bloque de código.

A continuación se muestra la sintaxis del bucle **while**.

```dart
while (expression) {
   Statement(s) to be executed if expression is true  
}
```

Un ejemplo seria el siguiente:

```dart
void main() { 
   int num = 5; 
   int factorial = 1; 
   
   while(num >=1) { 
      factorial = factorial * num; 
      num--; 
   } 
   print("The factorial  is ${factorial}"); 
}
```
