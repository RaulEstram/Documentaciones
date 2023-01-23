# Synchronized

La palabra clave synchronized es un mecanismo de control de acceso en Java que se utiliza para sincronizar el acceso a un recurso compartido entre varios threads. Cuando un thread intenta acceder a un método o bloque sincronizado, se adquiere un bloqueo sobre el objeto al que pertenece el método o bloque. Mientras el thread tenga el bloqueo, ningún otro thread podrá acceder al mismo método o bloque sincronizado en el mismo objeto.

La sincronización se utiliza para evitar problemas de concurrencia, como la lectura/escritura de un recurso compartido al mismo tiempo, o el acceso a un recurso no actualizado.

Existen dos formas de utilizar la palabra clave synchronized en Java:

1. Sincronizando un bloque: Se coloca la palabra clave synchronized antes de un bloque de código y se especifica el objeto sobre el cual se desea adquirir el bloqueo.

```java
synchronized(objeto) {
    // código a ejecutar
}
```

2. Sincronizando un método: Se coloca la palabra clave synchronized antes de la declaración del método. Todo el cuerpo del método será sincronizado.

```java
public synchronized void metodo(){
    // código a ejecutar
}
```

## Importancia de synchronized



## ejemplo:

* clase hilo

```java
package hilos;

import static hilos.Main.imprimirFrases;

public class EjemploSynchronizedThread implements Runnable {

    String frase1, frease2;

    public EjemploSynchronizedThread(String frase1, String frease2) {
        this.frase1 = frase1;
        this.frease2 = frease2;
    }

    @Override
    public void run() {
        imprimirFrases(this.frase1, this.frease2);
    }
}
```

* main con synchonized

```java
package hilos;

public class Main {

    public static void main(String[] args) throws InterruptedException {
        
        new Thread(new EjemploSynchronizedThread("hola", "hola2")).start();
        new Thread(new EjemploSynchronizedThread("pepe", "pepe2")).start();
        new Thread(new EjemploSynchronizedThread("raul", "raul2")).start();
        new Thread(new EjemploSynchronizedThread("meco", "meco2")).start();

    }
    
    public synchronized static void imprimirFrases(String frase1, String frase2){
        System.out.println("frase1 = " + frase1);
        try {
            Thread.sleep(500);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }
        System.out.println("frase2 = " + frase2);
    }
}
```

* resultado con synchronized

```shell
frase1 = hola
frase2 = hola2
frase1 = meco
frase2 = meco2
frase1 = raul
frase2 = raul2
frase1 = pepe
frase2 = pepe2
```


* resultado sin synchronized

```shell
frase1 = hola
frase1 = raul
frase1 = pepe
frase1 = meco
frase2 = hola2
frase2 = raul2
frase2 = meco2
frase2 = pepe2
```


> **Note** en pocas palabras el **synchronized** nos sirve para que un metodo o recurso no se utilice en diferentes hilos al mismo tiempo, los hilos esperan a que se desocupe este recurso para poder utilizarlo.
