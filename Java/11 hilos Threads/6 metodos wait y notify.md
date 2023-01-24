# Metodos wait y notify

para ver el funcionamiento de estos metodos usaremos el siguiente ejemplo:

> Nofity y wait solamente funcionan en recursos como métodos que sean synchronized

* modelo panaderia

```java
package ejemplosync.models;

public class Panaderia {

    private String pan;
    private boolean disponible;

    public synchronized void hornear(String masa) {
        while (disponible) {
            try {
                wait();
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
        }
        this.pan = masa;
        System.out.println("Panadero hornea: " + masa);
        disponible = true;
        notify();
    }

    public synchronized void consumir() {
        while (!disponible) {
            try {
                wait();
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
            System.out.println("Cliente consume el pan: " + this.pan);
            disponible = false;
            notify();
        }

    }

}
```

Este código es un ejemplo de cómo utilizar la sincronización en Java para controlar el acceso compartido a un recurso. La clase Panaderia tiene dos atributos privados: una cadena de texto "pan" y un booleano "disponible".

La clase tiene dos métodos públicos sincronizados: hornear y consumir. El método hornear se utiliza para "hornear" un pan y marcarlo como "disponible" para su consumo. El método consumir se utiliza para "consumir" un pan y marcarlo como "no disponible" para su consumo.

Ambos métodos utilizan un bucle while para verificar el estado de disponibilidad del pan. Si el pan está disponible, el método hornear espera a que el pan sea consumido antes de continuar (usando el método wait()). Si el pan no está disponible, el método consumir espera a que el pan sea horneado antes de continuar.

Una vez que el pan ha sido horneado o consumido, se utiliza el método notify() para notificar a cualquier otro hilo que esté esperando en el bucle while para continuar su ejecución.

En caso de una InterruptedException (que puede ocurrir si otro hilo interrumpe el hilo actual mientras espera), se lanza una excepción de tiempo de ejecución para indicar que algo salió mal.


* hilos que ejecutaran los metodos sincronizados

Panadero

```java
package ejemplosync.runnable;

import ejemplosync.models.Panaderia;

import java.util.concurrent.ThreadLocalRandom;

public class Panadero implements Runnable{

    private final Panaderia panaderia;

    public Panadero(Panaderia panaderia) {
        this.panaderia = panaderia;
    }

    @Override
    public void run() {
        for (int i = 0; i < 10; i++) {
            panaderia.hornear("Concha No. " + i);
            try {
                Thread.sleep(ThreadLocalRandom.current().nextInt(500, 2000));
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
        }
    }
}
```

Consumidor

```java
package ejemplosync.runnable;

import ejemplosync.models.Panaderia;

public class Consumidor implements Runnable{

    private final Panaderia panaderia;

    public Consumidor(Panaderia panaderia) {
        this.panaderia = panaderia;
    }

    @Override
    public void run() {
        for (int i = 0; i < 10; i++) {
            panaderia.consumir();
        }
    }
}
```

* main donde se llaman los hilos


```java
import ejemplosync.models.Panaderia;
import ejemplosync.runnable.Consumidor;
import ejemplosync.runnable.Panadero;

public class Main {

    public static void main(String[] args) {
        Panaderia panaderia = new Panaderia();
        new Thread(new Panadero(panaderia)).start();
        new Thread(new Consumidor(panaderia)).start();

    }
}
```

## Usar funcioens lambda

```java
import ejemplosync.models.Panaderia;
import ejemplosync.runnable.Consumidor;
import ejemplosync.runnable.Panadero;

import java.util.concurrent.ThreadLocalRandom;

public class Main {

    public static void main(String[] args) {
        Panaderia panaderia = new Panaderia();

        new Thread(()->{
            for (int i = 0; i < 10; i++) {
                panaderia.hornear("Concha No. " + i);
                try {
                    Thread.sleep(ThreadLocalRandom.current().nextInt(500, 2000));
                } catch (InterruptedException e) {
                    throw new RuntimeException(e);
                }
            }
        }).start();

        new Thread(()->{for (int i = 0; i < 10; i++) {
            panaderia.consumir();
        }}).start();
    }
}
```

En este caso solamente estariamos necesitando la clase Panaderia.