# Creacion de hilos con Thread y Runnable

Vamos a ver como crear unas clases basicas de hilos usando Thread y Runnable

## Thread

* clase que hereda Thread

```java
package hilos;

public class EjemploExtenerThread extends Thread {

    public EjemploExtenerThread() {
        super();
    }

    public EjemploExtenerThread(String name) {
        super(name);
    }

    @Override
    public void run() {
        super.run();
        System.out.println("Se inicia el método run del hilo: " + this.getName());

        for (int i = 0; i < 5; i++) {
            try {
                Thread.sleep(10);
                System.out.println(this.getName());
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
        }

        System.out.println("Se finalizo el hilo: " + this.getName());
    }
}
```

* Main

```java
import hilos.EjemploExtenerThread;

public class Main {

    public static void main(String[] args) throws InterruptedException {
        EjemploExtenerThread hilo = new EjemploExtenerThread();
        EjemploExtenerThread hilo2 = new EjemploExtenerThread("hilos 2");

        hilo.start();
        hilo2.start();

    }
}
```

* Salida

```shell
Se inicia el método run del hilo: hilos 2
Se inicia el método run del hilo: Thread-0
hilos 2
Thread-0
hilos 2
hilos 2
Thread-0
hilos 2
Thread-0
hilos 2
Se finalizo el hilo: hilos 2
Thread-0
Thread-0
Se finalizo el hilo: Thread-0
```


## Runnable

* clase que implementa Runnable

```java
package hilos;

public class EjemploRunnableHilos implements Runnable {

    private String nombre;

    public EjemploRunnableHilos(String nombre) {
        this.nombre = nombre;
    }

    @Override
    public void run() {
        System.out.println("Se inicia el método run del hilo: " + this.getNombre());

        for (int i = 0; i < 5; i++) {
            try {
                Thread.sleep(10);
                System.out.println(this.getNombre());
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
        }

        System.out.println("Se finalizo el hilo: " + this.getNombre());
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

}
```

* Main

```java
import hilos.EjemploRunnableHilos;

public class Main {

    public static void main(String[] args) throws InterruptedException {
        
        Thread hilo1 = new Thread(new EjemploRunnableHilos("hilo 1"));
        hilo1.start();
        new Thread(new EjemploRunnableHilos("hilo 2")).start();
        new Thread(new EjemploRunnableHilos("hilo 3")).start();
        new Thread(new EjemploRunnableHilos("hilo 4")).start();

    }
}
```

* Salida

```shell
Se inicia el método run del hilo: hilo 1
hilo 1
Se inicia el método run del hilo: hilo 2
Se inicia el método run del hilo: hilo 3
hilo 1
hilo 2
hilo 3
Se inicia el método run del hilo: hilo 4
hilo 1
hilo 2
hilo 3
Se finalizo el hilo: hilo 1
hilo 4
hilo 2
Se finalizo el hilo: hilo 2
hilo 3
Se finalizo el hilo: hilo 3
hilo 4
hilo 4
Se finalizo el hilo: hilo 4

Process finished with exit code 0
```

> **Note** Como podemos ver en las salidas de los 2 ejemplos, podemos apreciar el paralelismo, donde se ejecutan los 2 hilos al mismo tiempo.
