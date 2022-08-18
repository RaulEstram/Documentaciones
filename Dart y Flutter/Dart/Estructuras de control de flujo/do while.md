# Do - While

El ciclo do...while es similar al ciclo while excepto que el ciclo do...while no evalúa la condición la primera vez que se ejecuta el ciclo. 

Sin embargo, la condición se evalúa para las iteraciones posteriores. En otras palabras, el bloque de código se ejecutará al menos una vez en un ciclo do…while.


```dart
do {  
   Statement(s) to be executed;  
} while (expression); 
```

Un ejemplo seria el siguiente:

```dart
void main() { 
   var n = 100; 
   do { 
      print(n); 
   }
   while(n<10); 
}  
```