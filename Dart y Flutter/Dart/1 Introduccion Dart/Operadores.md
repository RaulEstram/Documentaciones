# Operadores

En Dart al igual que en varios lenguajes de programacion tenemos diferentes tipos de operadores como son:

* Operadores Aritmeticos
* Operadores de Asignacion
* Operadores relacionales
* Operador Ternario

## Operadores Aritmeticos

los operadores aritmeticos son los siguientes:

* ```+```
* ```-```
* ```/```
* ```*```
* ```%```
* ```++```
* ```--```
* ```+=```
* ```-=```

También tenemos otros no tan comunes como lo son:
* ```-``` expr, es usado para cambiar el valor de la expresión, por ejmplo 15 -> -15
* ```~/```, es usado para obtener la parte entera de una división.

## Operadores de Asignacion

Tenemos operadores de asignación comunes como:
* =

Pero también hay otros que no son comunes o que son únicos como es:
* ??=, el cual sirve para darle un valor a una variable en el caso de que sea null

ejemplo:

```
void main() {
  int? a;
  print(a); // null
  
  a ??= 5;
  print(a); // 5 
  
  int? b = 10;
  print(b); // 20
  
  b ??= 20;
  print(b); // 10   
}
```

Por otra parte tambien tenemos el operador **??** que es prácticamente lo mismo que el **??=** pero es para darle un valor directamente a una variable respecto a otras variables, por ejemplo:

```dart
void main(){
    int? x;
    int y = 20;
    int z = x ?? y ?? 69;
    print(z); // 20
}
```


## Operadores relacionales

tenemos operadores como:

* ```<```
* ```>```
* ```<=```
* ```>=```
* ```==```
* ```!=```
* ```is```, por ejemplo: ```i is int```
* ```is!```, por ejemplo: ```j is! Int```

## Operador ternario

Este operador es una simplificacion para el if - else en una sola linea cuando son pocas lineas, la sintaxis es la siguiente:

```dart
condicion ? doSomething : doSomething
```

tambien podemos tener operadores ternarios con mas de estos, por ejemplo:

```dart
(foo==1)?something1():(foo==2)? something2():(foo==3)? something3(): something4();
```

Que seria lo mismo que:

```dart
if(foo ==1){
    something1();
}
elseif(foo ==2){
    something2();
}
elseif(foo ==3){
    something3();
}
else something4();
```