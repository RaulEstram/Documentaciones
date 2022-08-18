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

