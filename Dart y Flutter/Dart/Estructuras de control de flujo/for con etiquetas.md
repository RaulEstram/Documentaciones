# For con etiquetas

Las etiquetas nos sirven para definir o darle un nombre a un **for** para después realizar un **break** a este, en el caso de que se estén utilizando **for anidados** o por alguna otra razón, veamos un ejemplo:

```dart
void main(){
  outerLoop:
  for (int i = 0; i < 10; i++) {
    innerLoop:
    for (int j = 0; j < 10; j++) {
      print('($i, $j)');
      if(i == 3 && j == 5){
        break outerLoop;
      }
    }
  }
}
```

El anterior codigo imprimiria lo siguiente:

```termianl
(0, 0)
(0, 1)
(0, 2)
(0, 3)
(0, 4)
(0, 5)
(0, 6)
(0, 7)
(0, 8)
(0, 9)
(1, 0)
(1, 1)
(1, 2)
(1, 3)
(1, 4)
(1, 5)
(1, 6)
(1, 7)
(1, 8)
(1, 9)
(2, 0)
(2, 1)
(2, 2)
(2, 3)
(2, 4)
(2, 5)
(2, 6)
(2, 7)
(2, 8)
(2, 9)
(3, 0)
(3, 1)
(3, 2)
(3, 3)
(3, 4)
(3, 5)
```