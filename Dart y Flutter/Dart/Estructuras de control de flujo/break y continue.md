# Break y Continue

## Brack

El uso de **break** en un ciclo hace que el programa salga del ciclo. A continuación se muestra un ejemplo de la instrucción **break**.

```dart
void main() { 
   int i = 1; 
   while(i<=100) { 
      if (i % 5 == 0) { 
         print("El primer multiplo de 5  entre el 1 y el 100 es : ${i}"); 
         break ;    
         //exit the loop if the first multiple is found 
      } 
      i++; 
   }
}  
```

El anterior codigo solamente imprimira:

```El primer multiplo de 5  entre el 1 y el 100 es : 5```


## continue

La declaración de **continue** omite las declaraciones subsiguientes en la iteración actual y lleva el control de regreso al comienzo del ciclo.

A diferencia de la sentencia break, la sentencia continue no sale del ciclo. Termina la iteración actual y comienza la iteración subsiguiente.

El siguiente ejemplo muestra cómo puede usar la declaración de **continue** en Dart:

```dart
void main() { 
   int num = 0; 
   int count = 0; 
   
   for(num = 0;num<=20;num++) { 
      if (num % 2==0) { 
         continue; 
      } 
      count++; 
   } 
   print("El numero de pares que hay entre el 0 y el 20 es de: ${count}"); 
}  
```

El anterior codigo imprimira:

```El numero de pares que hay entre el 0 y el 20 es de: 10```