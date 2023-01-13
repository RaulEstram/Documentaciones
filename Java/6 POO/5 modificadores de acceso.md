# Modificadores de acceso

Los modificadores de acceso en Java se utilizan para especificar el nivel de acceso a una clase, una variable, un método o un constructor. Los modificadores de acceso disponibles en Java son:

* **public**: permite el acceso desde cualquier parte del programa.
* **private**: permite el acceso solo desde la clase en la que se define.
* **protected**: permite el acceso desde la clase en la que se define y desde cualquier subclase.
* **default (sin modificador)**: permite el acceso desde la misma paquete en el que se define.

Si no se especifica ningún modificador de acceso, se considera como default



## Alcance de los modificadores de acceso


El alcance de los modificadores de acceso en Java se refiere a desde dónde se pueden acceder a las clases, variables, métodos o constructores a los que se aplican. Los cuatro modificadores de acceso disponibles en Java tienen diferentes alcances:

* `public`: permite el acceso desde cualquier parte del programa. Esto significa que las clases, variables, métodos o constructores marcados con public pueden ser accedidos desde cualquier clase, independientemente de su paquete o jerarquía de herencia.

* `private`: permite el acceso solo desde la clase en la que se define. Esto significa que las clases, variables, métodos o constructores marcados con private solo pueden ser accedidos desde la clase en la que se definen, no desde ninguna otra clase, ni desde subclases.

* `protected`: permite el acceso desde la clase en la que se define y desde cualquier subclase. Esto significa que las clases, variables, métodos o constructores marcados con protected pueden ser accedidos desde la clase en la que se definen y desde cualquier subclase, pero no desde otras clases en el mismo paquete.

* `default` (sin modificador): permite el acceso desde la misma paquete en el que se define. Esto significa que las clases, variables, métodos o constructores marcados con default pueden ser accedidos desde cualquier clase en el mismo paquete, pero no desde clases en paquetes diferentes.

En resumen, el alcance de los modificadores de acceso en Java va desde **el más restringido (private) hasta el más amplio (public)** y se utilizan para controlar el acceso a los miembros de una clase y asegurar la encapsulación de la misma.