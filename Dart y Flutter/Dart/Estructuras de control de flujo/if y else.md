# If - else.

**if** es una estructura de control que comprueba si la condición o expresión que se le pasa es verdadera o falsa.

Si la condición es verdadera, se ejecuta él condigo dentro de la sentencia **if**. En caso contrario realiza la siguiente comprobación que está en el **else if**, por último tenemos el **else** que es lo que ejecutara si ninguna condición es verdadera.

A continuación se muestra la sintaxis del bucle **if - else if - else**.


```dart
if (boolean_expression1) { 
   //statements if the expression1 evaluates to true 
} 
else if (boolean_expression2) { 
   //statements if the expression2 evaluates to true 
} 
else { 
   //statements if both expression1 and expression2 result to false 
} 
```

> **Nota** se pueden poner cuantos **else if** se quieran:

Un ejemplo de if - else if - else, es el siguiente:

```dart
void main() {
  int edad = -1;
  
  if (edad < 18 && edad >= 0){
    print("Eres menor de edad.");
  } else if (edad >= 18){
    print("Eres mayor de edad.");
  } else {
    print("Tu edad es negativa, por lo que no es posible.");
  }
}
```