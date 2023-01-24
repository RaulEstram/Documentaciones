# Framework Executor

**Executor** es una interfaz en Java que proporciona una forma de ejecutar tareas en segundo plano. Se utiliza para crear y controlar un conjunto de hilos de ejecución que realizan tareas.

La interfaz **Executor** define un solo método, `execute(Runnable command)`, que recibe un objeto **Runnable** y lo ejecuta en un hilo de ejecución.

La interfaz **Executor** es útil para separar la lógica de creación y control de hilos de la lógica de negocio de la aplicación. En lugar de crear y controlar hilos directamente en el código de la aplicación, se pueden delegar estas tareas al **Executor**. Esto permite una mayor flexibilidad y escalabilidad en la aplicación, ya que se puede cambiar fácilmente la implementación del **Executor** sin afectar al código de la aplicación.

Java proporciona varias implementaciones de **Executor** en su biblioteca estándar, como **Executors**, que proporciona métodos estáticos para crear diferentes tipos de **Executor**, como **Executor** que utiliza un pool de hilos fijo o un pool de hilos que se adapta dinámicamente al número de tareas pendientes.

En resumen **Executor** es una interfaz que proporciona una forma de ejecutar tareas en segundo plano, se utiliza para crear y controlar un conjunto de hilos de ejecución que realizan tareas, ayudando a separar la lógica de creación y control de hilos de la lógica de negocio de la aplicación, proporcionando una mayor flexibilidad y escalabilidad en la aplicación.

## Executor y ExecutorService

Executor y ExecutorService son interfaces relacionadas en Java que se utilizan para crear y controlar hilos de ejecución.

Executor es una interfaz más genérica que define un solo método, execute(Runnable command), que recibe un objeto Runnable y lo ejecuta en un hilo de ejecución. El Executor no proporciona una forma de cancelar o monitorear las tareas en ejecución.

ExecutorService, por otro lado, es una interfaz más específica que extiende a Executor. Además de execute, proporciona métodos adicionales para cancelar tareas, monitorear el estado de las tareas y esperar a que las tareas se completen. ExecutorService también proporciona una forma de enviar tareas que devuelven un valor, mediante la utilización de objetos Future.

En resumen, Executor es una interfaz más genérica que proporciona una forma de ejecutar tareas en segundo plano, mientras que ExecutorService es una interfaz más específica que proporciona una forma de ejecutar, cancelar y monitorear tareas en segundo plano, y también proporciona una forma de enviar tareas que devuelven un valor.

## Ejemplo uso de ExecutorService

```java
package ejemploexecutor;

import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.TimeUnit;

public class EjemploSinlgeThreadExcutor {

    public static void main(String[] args) throws InterruptedException {
        // hay 2 tipos de Executor
        ExecutorService executorService = Executors.newSingleThreadExecutor();

        Runnable tarea = () -> {
            System.out.println("Inicio Tarea");
            try {
                System.out.println(Thread.currentThread().getName());
                TimeUnit.SECONDS.sleep(1);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
                throw new RuntimeException(e);
            }
            System.out.println("Fin Tarea");
        };


        executorService.submit(tarea);
        executorService.shutdown();
        
        // sin el awaitTermination se imprimiría primero él hola y después lo de la tarea.
        executorService.awaitTermination(2, TimeUnit.SECONDS);
        System.out.println("hola");
    }
}

```

awaitTermination() es un método de la interfaz ExecutorService en Java, que espera a que todas las tareas enviadas al ExecutorService se completen antes de continuar. Este método toma dos parámetros: uno es el tiempo en milisegundos que se esperará antes de detener la espera, y el segundo es el tiempo de espera en unidades de tiempo.

El método awaitTermination() es útil para asegurarse de que todas las tareas enviadas al ExecutorService hayan terminado antes de continuar con otras operaciones en la aplicación. Por ejemplo, una aplicación puede utilizar este método para esperar a que todas las tareas enviadas al ExecutorService se completen antes de cerrar la aplicación o antes de realizar una operación que depende de los resultados de las tareas enviadas.

Es importante tener en cuenta que si el tiempo de espera se agota antes de que todas las tareas se completen, el método awaitTermination() devuelve false, indicando que no se completaron todas las tareas y que algunas tareas pueden seguir ejecutándose.

En resumen awaitTermination() es un método de la interfaz ExecutorService en Java, que espera a que todas las tareas enviadas al ExecutorService se completen antes de continuar, es útil para asegurarse de que todas las tareas enviadas al ExecutorService hayan terminado antes de continuar con otras operaciones en la aplicación.
