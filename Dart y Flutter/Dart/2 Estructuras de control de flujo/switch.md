# Switch

La declaración de **swithc** evalúa una expresión, hace coincidir el valor de la expresión con una cláusula de caso y ejecuta las declaraciones asociadas con ese caso.

A continuación se muestra la sintaxis.

```dart
switch(variable_expression) { 
   case constant_expr1: { 
      // statements; 
   } 
   break; 
  
   case constant_expr2: { 
      //statements; 
   } 
   break; 
      
   default: { 
      //statements;  
   }
   break; 
} 
```

A continuacion un ejemplo:

```dart
void main() { 
   String grade = "A"; 
   switch(grade) { 
      case "A": {  print("Excellent"); } 
      break; 
     
      case "B": {  print("Good"); } 
      break; 
     
      case "C": {  print("Fair"); } 
      break; 
     
      case "D": {  print("Poor"); } 
      break; 
     
      default: { print("Invalid choice"); } 
      break; 
   } 
}  
```