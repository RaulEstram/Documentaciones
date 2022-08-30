# Funciones Parametrizadas

Una función parametrizada es aquella que tiene parámetros, y para saber que es un parámetro tenemos los siguientes puntos:

Los parámetros son un mecanismo para pasar valores a funciones. 
Los parámetros forman parte de la firma de la función. 
Los valores de los parámetros se pasan a la función durante su invocación.

La sintaxis básica para las funciones parametrizadas es la siguiente:

```dart
Function_name(data_type param_1, data_type param_2[…]) { 
   //statements 
}
```

Hay diferentes formas de definir los parámetros de una función, las cuales se pueden combinar entre sí para crear funciones parametrizadas complejas. Las formas de definir parámetros son las siguientes:

* Parámetros posicionales requeridos
* Parámetro posicional opcional
* Parámetro con nombre opcional
* Parámetros opcionales con valores predeterminados

## Parámetros posicionales requeridos

Es obligatorio pasar valores a los parámetros requeridos durante la llamada a la función.

Su sintaxis es la siguiente:

```dart
Function_name(data_type param_1, data_type param_2[…]) { 
   //statements 
}
```

Un ejemplo sería el siguiente código:

```dart
void main() { 
   testParam(123,"this is a string"); 
}  
testParam(int n1,String s1) { 
   print(n1); 
   print(s1); 
} 
```


## Parámetro posicional opcional

Para especificar parámetros posicionales opcionales, utilizaremos corchetes [].

Si a un parámetro opcional no se le pasa un valor, se establece en NULL.

Su sintaxis es la siguiente:

```dart
void function_name(param1, [optional_param_1, optional_param_2]) { 
    //statements
} 
```

Un ejemplo sería el siguiente código:

```dart
void main() { 
   testParam(123); 
}

void testParam(int n1, [s1]) { 
   print(n1); 
   print(s1); 
} 
```

Su salida seria la siguiente:

```terminal
123
null
```

> **Note** Los parámetros posicionales opcionales no se les puede definir el tipo de dato que se les tienes que pasar a diferencia de los parámetros posicionales requeridos.

## Parámetro con nombre opcional

A diferencia de los parámetros posicionales, el nombre de los parámetros debe especificarse mientras se pasa el valor. Las llaves {} se pueden usar para especificar parámetros con nombre opcionales.


Su sintaxis es la siguiente:

```dart
void function_name(a, {optional_param1, optional_param2}) { 
    //statements
} 
```

Un ejemplo sería el siguiente código:

```dart
void main() { 
   testParam(123); 
   testParam(123,s1:'hello'); 
   testParam(123,s2:'hello',s1:'world'); 
}  

void testParam(n1,{s1,s2}) { 
   print(n1); 
   print(s1); 
}  
```

Su salida seria la siguiente:

```terminal
123
null
123
hello
123
world
```

## Parámetros opcionales con valores predeterminados

A los parámetros de función también se les pueden asignar valores por defecto. Sin embargo, dichos parámetros también pueden ser valores pasados ​​explícitamente.

Su sintaxis es la siguiente:

```dart
function_name(param1,{param2 = default_value}) { 
   //...... 
} 
```

Un ejemplo sería el siguiente código:

```dart
void main() { 
   testParam(123); 
}  
void testParam(n1,{s1=12}) { 
   print(n1); 
   print(s1); 
}   
```

Su salida seria la siguiente:

```terminal
123
12
```

## Argumentos con ?

Cuando agregamos un **?** al tipo de dato de un parámetro, hacemos referencia a que puede tener un null, en caso de **parámetros posicionales requeridos** y los **parámetro con nombre opcional**.

Si **no es un argumento opcional tenemos que pasar manualmente el null**, en el caso de que sea en los **parámetro con nombre opcional no es necesario ponerlo manualmente**.



Un ejemplo seria el siguiente:

```dart
void main() { 
   testParam(null); 
}  

void testParam(int? n1, {String? s1}) { 
  print(n1); 
  print(s1);
}   
```

## Combinacion de tipos de parametros

Por último, hay que mencionar que no es posible combinar todos los tipos de parámetros, pero si es posible combinar algunos, por ejemplo, tener las siguientes combinaciones. 

* Parámetros posicionales requeridos y Parámetro posicional opcional
* Parámetros posicionales requeridos y Parámetro con nombre opcional
* Parámetros posicionales requeridos y Parámetros opcionales con valores predeterminados
* Parámetros posicionales requeridos, Parámetro con nombre opcional y Parámetros opcionales con valores predeterminados