# Future

En el contexto de **ExecutorService**, **Future** es una interfaz que representa una tarea que se ejecuta en segundo plano y puede devolver un valor. El objeto **Future** proporciona una forma de recuperar el resultado de una tarea en ejecución o cancelar la tarea.

Cuando se envía una tarea al **ExecutorService** mediante el método `submit(Callable<T> task)` o `submit(Runnable task, T result)`, el **ExecutorService** devuelve un objeto **Future** que representa la tarea en ejecución. El objeto **Future** proporciona varios métodos para interactuar con la tarea en ejecución, como:

* `cancel(boolean mayInterruptIfRunning)`: Cancela la tarea en ejecución.
* `isCancelled()`: Devuelve true si la tarea se ha cancelado, false en caso contrario.
* `isDone()`: Devuelve true si la tarea ha finalizado, ya sea normalmente o debido a una cancelación.
* `get()`: Devuelve el resultado de la tarea. Este método bloquea los procesos hasta que la tarea se complete.
* `get(long timeout, TimeUnit unit)`: Devuelve el resultado de la tarea. Este método bloquea hasta que la tarea se complete o hasta que el tiempo de espera se agote. (util para evitar que un proceso tome mas tiempo de lo esperado por algun fallo o algo por el estilo)

En resumen, **Future** es una interfaz que representa una tarea que se ejecuta en segundo plano y puede devolver un valor. Al enviar una tarea al **ExecutorService** mediante el método `submit(Callable<T> task)` o `submit(Runnable task, T result)`, el **ExecutorService** devuelve un objeto **Future** que representa la tarea en ejecución, el objeto **Future** proporciona varios métodos para interactuar con la tarea en ejecución, como cancelar, verificar si está completa o recuperar el resultado de la tarea.


## Ejemplo con Runnable

```java
package ejemploexecutor;

import java.util.concurrent.*;

public class EjemploSinlgeThreadExecutor {

    public static void main(String[] args) throws InterruptedException, ExecutionException, TimeoutException {
        // hay 2 tipos de Executor
        ExecutorService executorService = Executors.newSingleThreadExecutor();

        Runnable tarea = () -> {
            System.out.println("Inicio Tarea");
            try {
                System.out.println(Thread.currentThread().getName());
                TimeUnit.SECONDS.sleep(3);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
                throw new RuntimeException(e);
            }
            System.out.println("Fin Tarea");
        };


        Future<?> resultado = executorService.submit(tarea);
        executorService.shutdown();

        while (!resultado.isDone()){
            System.out.println("Esperando a que termine la tarea");
            TimeUnit.MILLISECONDS.sleep(500);
        }

        System.out.println(resultado.get(5, TimeUnit.SECONDS));
        System.out.println(resultado.isDone());

    }
}
```


## Ejemplo con Callable

```java
package ejemploexecutor;

import java.util.concurrent.*;

public class EjemploSinlgeThreadExecutor {

    public static void main(String[] args) throws InterruptedException, ExecutionException, TimeoutException {
        // hay 2 tipos de Executor
        ExecutorService executorService = Executors.newSingleThreadExecutor();

        // marcamos el tipo de datos que regresa
        Callable<String> tarea = () -> {
            System.out.println("Inicio Tarea");
            try {
                System.out.println(Thread.currentThread().getName());
                TimeUnit.SECONDS.sleep(3);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
                throw new RuntimeException(e);
            }
            System.out.println("Fin Tarea");
            return "{alguan respuesta tipo REST API}";
        };

        // marcamos el tipo de dato que recibimos
        Future<String> resultado = executorService.submit(tarea);
        executorService.shutdown();

        while (!resultado.isDone()){
            System.out.println("Esperando a que termine la tarea");
            TimeUnit.MILLISECONDS.sleep(500);
        }

        System.out.println(resultado.get(5, TimeUnit.SECONDS));
        System.out.println(resultado.isDone());

    }
}
```

> Callable nos permite regresar un valor, mientras que Runnable no nos lo permite