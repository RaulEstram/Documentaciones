# Furutes con Executor 

Executor nos permite realizar varios procesos en hilos y nos regresan un Future como se vio en la anterior leccion.

En esta seccion veremos 2 tipos de Executor para realizar estos procesos en hilos, ya sea de forma ordenada o de manera simultanea.

## newSingleThreadExecutor() - Ejecucion de procesos de forma ordenada

`newSingleThreadExecutor()` nos permite ejecutar varios procesos en hilos de forma ordenada. 

Primero se tiene que terminar el proceso o tarea que se le asignó al principio para continuar con el segundo y así sucesivamente.


```java
package ejemploexecutor;

import java.util.concurrent.*;

public class EjemploSinlgeThreadExcutor {

    public static void main(String[] args) throws InterruptedException {
        // creamos nuestro Executor
        ExecutorService executorService = Executors.newSingleThreadExecutor();
        
        // Creamos los procesos que se ejecutaran en hilos:
        Callable<String> tarea1 = () -> {
            System.out.println("Inicio de la tarea No. 1");
            TimeUnit.SECONDS.sleep(ThreadLocalRandom.current().nextInt(1, 4));
            return "Resultado de la tarea 1";
        };

        Callable<String> tarea2 = () -> {
            System.out.println("Inicio de la tarea No. 2");
            TimeUnit.SECONDS.sleep(ThreadLocalRandom.current().nextInt(1, 4));
            return "Resultado de la tarea 2";
        };

        Callable<Integer> tarea3 = () -> {
            System.out.println("Inicio de la tarea No. 3");
            TimeUnit.SECONDS.sleep(ThreadLocalRandom.current().nextInt(1, 4));
            return 69;
        };


        Future<String> response1 = executorService.submit(tarea1);
        Future<String> response2 = executorService.submit(tarea2);
        Future<Integer> response3 = executorService.submit(tarea3);

        while (!(response1.isDone() && response2.isDone() && response3.isDone())) {
            imprimirProgreso(response1, response2, response3);
            TimeUnit.MILLISECONDS.sleep(500);
        }

        imprimirProgreso(response1, response2, response3);
        System.out.println("finalizaron los procesos");
        executorService.shutdown();
    }

    public static void imprimirProgreso(Future<?> response1, Future<?> response2, Future<?> response3) {
        System.out.printf("response 1: %s - response 2: %s - response 3: %s%n",
                response1.isDone() ? "Finalizo" : "En proceso",
                response2.isDone() ? "Finalizo" : "En proceso",
                response3.isDone() ? "Finalizo" : "En proceso");
    }
}
```

## newFixedThreadPool(n) - Ejecucion de multiples procesos de forma paralela

`newFixedThreadPool(n)` nos permite ejecutar varios procesos en hilos de forma simultanea.

n es el numero de procesos simultaneos que puede realizar aunque se le pueden agregar mas y se agregaran a la cola.

```java
package ejemploexecutor;

import java.util.concurrent.*;

public class EjemploSinlgeThreadExcutor {

    public static void main(String[] args) throws InterruptedException {
        // creamos nuestro Executor
        ExecutorService executorService = Executors.newFixedThreadPool(3);

        // Creamos los procesos que se ejecutaran en hilos:
        Callable<String> tarea1 = () -> {
            System.out.println("Inicio de la tarea No. 1");
            TimeUnit.SECONDS.sleep(ThreadLocalRandom.current().nextInt(1, 4));
            return "Resultado de la tarea 1";
        };

        Callable<String> tarea2 = () -> {
            System.out.println("Inicio de la tarea No. 2");
            TimeUnit.SECONDS.sleep(ThreadLocalRandom.current().nextInt(1, 4));
            return "Resultado de la tarea 2";
        };

        Callable<Integer> tarea3 = () -> {
            System.out.println("Inicio de la tarea No. 3");
            TimeUnit.SECONDS.sleep(ThreadLocalRandom.current().nextInt(1, 4));
            return 69;
        };

        Callable<Integer> tarea4 = () -> {
            System.out.println("Inicio de la tarea No. 4");
            TimeUnit.SECONDS.sleep(ThreadLocalRandom.current().nextInt(1, 4));
            return 69;
        };

        Future<String> response1 = executorService.submit(tarea1);
        Future<String> response2 = executorService.submit(tarea2);
        Future<Integer> response3 = executorService.submit(tarea3);
        Future<Integer> response4 = executorService.submit(tarea4);

        while (!(response1.isDone() && response2.isDone() && response3.isDone())) {
            imprimirProgreso(response1, response2, response3);
            TimeUnit.MILLISECONDS.sleep(500);
        }

        imprimirProgreso(response1, response2, response3);
        System.out.println("finalizaron los procesos");
        executorService.shutdown();
    }

    public static void imprimirProgreso(Future<?> response1, Future<?> response2, Future<?> response3) {
        System.out.printf("response 1: %s - response 2: %s - response 3: %s%n",
                response1.isDone() ? "Finalizo" : "En proceso",
                response2.isDone() ? "Finalizo" : "En proceso",
                response3.isDone() ? "Finalizo" : "En proceso");
    }
}
```


En el siguiente codigo podemos apreciar mejor como trabaja este tipo de Executor:

```java
package ejemploexecutor;

import java.util.concurrent.*;

public class EjemploSinlgeThreadExcutor {

    public static void main(String[] args) throws InterruptedException {
        // creamos nuestro Executor
        ThreadPoolExecutor executorService = (ThreadPoolExecutor) Executors.newFixedThreadPool(3);
        System.err.println("executorService.getPoolSize() = " + executorService.getPoolSize());
        System.err.println("executorService.getQueue() = " + executorService.getQueue().size());
        // Creamos los procesos que se ejecutaran en hilos:
        Callable<String> tarea1 = () -> {
            System.out.println("Inicio de la tarea No. 1");
            TimeUnit.SECONDS.sleep(ThreadLocalRandom.current().nextInt(1, 4));
            return "Resultado de la tarea 1";
        };

        Callable<String> tarea2 = () -> {
            System.out.println("Inicio de la tarea No. 2");
            TimeUnit.SECONDS.sleep(ThreadLocalRandom.current().nextInt(1, 4));
            return "Resultado de la tarea 2";
        };

        Callable<Integer> tarea3 = () -> {
            System.out.println("Inicio de la tarea No. 3");
            TimeUnit.SECONDS.sleep(ThreadLocalRandom.current().nextInt(1, 4));
            return 69;
        };

        Callable<Integer> tarea4 = () -> {
            System.out.println("Inicio de la tarea No. 4");
            TimeUnit.SECONDS.sleep(ThreadLocalRandom.current().nextInt(1, 4));
            return 69;
        };

        Future<String> response1 = executorService.submit(tarea1);
        Future<String> response2 = executorService.submit(tarea2);
        Future<Integer> response3 = executorService.submit(tarea3);
        Future<Integer> response4 = executorService.submit(tarea4);

        System.err.println("executorService.getPoolSize() = " + executorService.getPoolSize());
        System.err.println("executorService.getQueue() = " + executorService.getQueue().size());

        while (!(response1.isDone() && response2.isDone() && response3.isDone())) {
            imprimirProgreso(response1, response2, response3);
            TimeUnit.MILLISECONDS.sleep(500);
        }

        imprimirProgreso(response1, response2, response3);
        System.out.println("finalizaron los procesos");
        executorService.shutdown();
    }

    public static void imprimirProgreso(Future<?> response1, Future<?> response2, Future<?> response3) {
        System.out.printf("response 1: %s - response 2: %s - response 3: %s%n",
                response1.isDone() ? "Finalizo" : "En proceso",
                response2.isDone() ? "Finalizo" : "En proceso",
                response3.isDone() ? "Finalizo" : "En proceso");
    }
}
```


## newScheduledThreadPool - Tareas con retraso

```java
package ejemploexecutor;

import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import java.util.concurrent.ScheduledExecutorService;
import java.util.concurrent.TimeUnit;

public class EjemploScheduledThreadPool {

    public static void main(String[] args) throws InterruptedException {
        // creamos nuestro Executor
        ScheduledExecutorService executorService = Executors.newScheduledThreadPool(2);

        System.out.println("Alguna tarea en el main ...");

        executorService.schedule(() -> {
            try {
                TimeUnit.SECONDS.sleep(2);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
            System.out.println("Hola mundo Tarea");
        }, 0, TimeUnit.MILLISECONDS);


        System.out.println("Alguna otra tarea en el main");
        executorService.shutdown();

    }
}
```


## scheduleAtFixedRate y scheduleWithFixedDelay  - Tareas repetitivas

**scheduleAtFixedRate** y **scheduleWithFixedDelay** son dos métodos en Java para programar tareas que se ejecutan periódicamente en un hilo de ejecución específico.

* **scheduleAtFixedRate** se utiliza para programar una tarea para ejecutarse con una frecuencia específica. El tiempo entre cada ejecución de la tarea comienza a contar desde el momento en que se completa la ejecución anterior. Si la ejecución de la tarea tarda más de lo previsto, las tareas siguientes se acumularán y se ejecutarán una detrás de la otra.

* **scheduleWithFixedDelay** se utiliza para programar una tarea para ejecutarse con un intervalo específico de tiempo entre cada ejecución. El tiempo entre cada ejecución de la tarea comienza a contar desde el momento en que se completa la ejecución anterior. Si la ejecución de la tarea tarda más de lo previsto, la siguiente tarea se programará para ejecutarse después del tiempo de retraso especificado, independientemente de cuánto tiempo tomó la ejecución anterior.

En resumen, **scheduleAtFixedRate** se utiliza para programar una tarea con una frecuencia específica, mientras que **scheduleWithFixedDelay** se utiliza para programar una tarea con un intervalo específico de tiempo entre cada ejecución.

### Ejemplo con codigo

Una tarea se pude repetir de las siguiente maneras:

* De forma infinita: simplemente quitamos en shutdown

```java
package ejemploexecutor;

import java.util.concurrent.Executors;
import java.util.concurrent.ScheduledExecutorService;
import java.util.concurrent.TimeUnit;

public class EjemploScheduledThreadPool {

    public static void main(String[] args) throws InterruptedException {
        // creamos nuestro Executor
        ScheduledExecutorService executorService = Executors.newScheduledThreadPool(2);

        System.out.println("Alguna tarea en el main ...");

        executorService.scheduleAtFixedRate(() -> {
            try {
                TimeUnit.SECONDS.sleep(2);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("Hola mundo Tarea");
        }, 0, 3000, TimeUnit.MILLISECONDS);


        System.out.println("Alguna otra tarea en el main");

        // para que se ejecute esta tarea de forma infinita quitamos el shutdown()
        //executorService.shutdown();
    }
}
```

* de forma que solamente se repita por x tiempo:

```java
package ejemploexecutor;

import java.util.concurrent.Executors;
import java.util.concurrent.ScheduledExecutorService;
import java.util.concurrent.TimeUnit;

public class EjemploScheduledThreadPool {

    public static void main(String[] args) throws InterruptedException {
        // creamos nuestro Executor
        ScheduledExecutorService executorService = Executors.newScheduledThreadPool(2);

        System.out.println("Alguna tarea en el main ...");

        executorService.scheduleAtFixedRate(() -> {
            try {
                TimeUnit.SECONDS.sleep(2);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
            System.out.println("Hola mundo Tarea");
        }, 0, 3000, TimeUnit.MILLISECONDS);

        // realizar la tarea durante un tiempo en específico
        TimeUnit.SECONDS.sleep(5);

        System.out.println("Alguna otra tarea en el main");

        executorService.shutdown();

    }
}
```

* que se ejecute x cantidad de veces, en este caso con CountDownLatch que nos sirve para hacer ocnteos con hilos y demas.

```java
package ejemploexecutor;

import java.util.concurrent.*;

public class EjemploScheduledThreadPool {

    public static void main(String[] args) throws InterruptedException {
        // creamos nuestro Executor
        ScheduledExecutorService executorService = Executors.newScheduledThreadPool(2);

        System.out.println("Alguna tarea en el main ...");

        // realizar una x cantidad de veces
        CountDownLatch lock = new CountDownLatch(5);

        Future<?> response = executorService.scheduleAtFixedRate(() -> {
            try {
                TimeUnit.SECONDS.sleep(2);
                // realizamos un i-- en lock practicamente
                lock.countDown();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("Hola mundo Tarea");
        }, 0, 3000, TimeUnit.MILLISECONDS);

        // quedamos a la espera hasta que lock llegue a 0
        lock.await();
        // forma educada de terminar una tarea.
        response.cancel(true);


        System.out.println("Alguna otra tarea en el main");

        executorService.shutdown();

    }
}
```

Ahora usando Atomic

```java
package ejemploexecutor;

import java.util.concurrent.*;
import java.util.concurrent.atomic.AtomicInteger;

public class EjemploScheduledThreadPool {

    public static void main(String[] args) throws InterruptedException {
        // creamos nuestro Executor
        ScheduledExecutorService executorService = Executors.newScheduledThreadPool(2);

        System.out.println("Alguna tarea en el main ...");

        // realizar una x cantidad de veces
        AtomicInteger contador = new AtomicInteger(5);
        Future<?> response = executorService.scheduleAtFixedRate(() -> {
            try {
                TimeUnit.SECONDS.sleep(2);
                // realizamos un i-- en lock practicamente
                contador.getAndDecrement();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("Hola mundo Tarea");
        }, 0, 3000, TimeUnit.MILLISECONDS);

        // quedamos a la espera hasta que lock llegue a 0

        while (contador.get() >= 0){
            if (contador.get() == 0){
                response.cancel(true);
                break;
            }
        }

        System.out.println("Alguna otra tarea en el main");

        executorService.shutdown();

    }
}
```