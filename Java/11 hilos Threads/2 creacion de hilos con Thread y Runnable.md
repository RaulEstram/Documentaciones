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
