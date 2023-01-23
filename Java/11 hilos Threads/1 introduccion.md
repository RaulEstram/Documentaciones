# Hilos o Threads

Los threads en Java son una forma de ejecutar varios procesos de manera concurrente dentro de un programa. Cada hilo es una instancia de la clase Thread o una subclase de ella. Cada hilo tiene su propio stack de ejecución y su propio puntero de instrucción, lo que permite que varios hilos ejecuten código de manera simultánea en un sistema multinúcleo. Los hilos también pueden comunicarse entre sí y compartir recursos, como variables y objetos. Los hilos son útiles para crear aplicaciones concurrentes, como juegos, aplicaciones de red y aplicaciones de interfaz de usuario.


## ¿Qué es un proceso?

En el contexto de los threads en Java, un proceso es una tarea o un conjunto de instrucciones que se ejecutan en un sistema operativo. Un proceso tiene su propio espacio de memoria y su propio conjunto de recursos del sistema, como archivos abiertos y conexiones de red. Cada vez que se ejecuta una aplicación en un sistema operativo, se crea un proceso para esa aplicación.

En la programación concurrente, se pueden crear varios procesos (threads) dentro de una misma aplicación para ejecutar varias tareas al mismo tiempo. Cada thread tiene su propia pila de ejecución y su propio puntero de instrucción, lo que permite que varios threads ejecuten código de manera simultánea en un sistema multinúcleo.

En resumen, un proceso es una tarea o conjunto de instrucciones que se ejecutan en un sistema operativo y un thread es una instancia de la clase Thread o una subclase de ella, que permite la ejecución concurrente de varios procesos dentro de una misma aplicación.

## Concurrencia y paralelismo

La concurrencia se refiere a la capacidad de un programa para ejecutar varios procesos de manera simultánea. En Java, esto se logra mediante el uso de threads. Los threads permiten que varios procesos se ejecuten de manera concurrente dentro de una sola aplicación.

El paralelismo se refiere a la capacidad de un programa para ejecutar varios procesos de manera simultánea en diferentes núcleos o procesadores. En Java, el paralelismo se logra mediante el uso de múltiples threads que se ejecutan en diferentes núcleos. El paralelismo es una forma de aprovechar al máximo el poder de procesamiento de un sistema, ya que permite que varios procesos se ejecuten al mismo tiempo, aumentando la velocidad de la aplicación. Sin embargo, es importante tener en cuenta que la programación concurrente y paralela tiene sus propios desafíos, como el control de acceso a los recursos compartidos y la sincronización de los threads.

> En pocas palabras si tenemos un solo core podemos usar concurrencia y si tenemos varios podemos usar paralelismo.

## Ejemplo de como crear un Thread/hilo con la clase Thread (Menos recomendada) 

Para crear un hilo en Java muy basico tenemos quee hacer los siguientes pasos:

1. Crear una clase que extienda de la clase `Thread`:

```java
class MiHilo extends Thread {
    public void run() {
        // código a ejecutar en el hilo
    }
}
```

2. Crear una instancia de la clase `MiHilo`:


```java
MiHilo hilo = new MiHilo();
```

3. Iniciar el hilo con el método `start()`:

```java
hilo.start();
```

En este ejemplo, estamos creando una clase llamada `MiHilo` que extiende de la clase `Thread`. La clase `MiHilo` tiene un método llamado `run()` que contiene el código que se ejecutará en el hilo. Luego, creamos una instancia de la clase `MiHilo` y la iniciamos con el método `start()`. Una vez que se llama al método `start()`, el hilo comenzará a ejecutar el código en el método `run()` de manera concurrente con el resto del programa.

> **Note** Como tal nosotros no vamos a utilizar el metodo `run()` lo va a ejecutar o administrar el metodo `start()`


## Ejemplo de como crear un Thread/hilo con la interfaz Runnable (Más recomendada) 

Para crear un hilo en Java muy basico tenemos quee hacer los siguientes pasos:

1. Crear una clase que implemente la interfaz `Runnable`:

```java
class MiHiloRunnable implements Runnable {
    public void run() {
        // código a ejecutar en el hilo
    }
}
```

2. Crear una instancia de la clase `Thread` y pasarle como argumento la instancia de `MiHiloRunnable`:

```java
MiHiloRunnable hiloRunnable = new MiHiloRunnable();
Thread hilo = new Thread(hiloRunnable);
```

3. Iniciar el hilo con el método `start()`:

```java
hilo.start();
```

En este ejemplo, estamos creando una clase llamada `MiHiloRunnable` que implementa la interfaz Runnable. La clase `MiHiloRunnable` tiene un método llamado `run()` que contiene el código que se ejecutará en el hilo. Luego, creamos una instancia de la clase `MiHiloRunnable` y la pasamos como argumento al constructor de la clase `Thread`. Finalmente, iniciamos el hilo con el método `start()`. Una vez que se llama al método `start()`, el hilo comenzará a ejecutar el código en el método `run()` de manera concurrente con el resto del programa.

Implementar la interfaz `Runnable` es una buena práctica cuando no deseas extender la clase `Thread` ya que esta solo permite extender una clase a la vez. Al implementar la interfaz `Runnable`, tu clase puede extender otra clase y aun así poder crear un hilo.


> **Note** esta manera de crear hilos es compatible con Java 8.

## Runnable vs Thread

Existen varias razones por las que es recomendable usar `Runnable` en lugar de extender la clase `Thread`:

* La herencia multiple es limitada en Java, eso significa que una clase solo puede extender una sola clase, pero puede implementar varias interfaces, al utilizar `Runnable`, tu clase puede extender otra clase y aun así poder crear un hilo.

* Al usar `Runnable`, tu clase está desacoplada de la clase `Thread` y puede ser utilizada en otros contextos donde no se requiera la creación de un hilo.

* `Runnable` proporciona una forma más limpia de crear un hilo, ya que el código relacionado con la creación de un hilo se encuentra en una clase separada (`Thread`) y el código que se ejecutará en el hilo se encuentra en otra clase (`Runnable`), lo que facilita la lectura y el mantenimiento del código.

* Utilizar `Runnable` permite que varias instancias de una misma clase sean utilizadas como hilos diferentes, mientras que al extender `Thread` solo se puede crear una instancia de la clase.

En resumen, utilizar `Runnable` es una mejor práctica ya que permite una mayor flexibilidad y reutilización del código, y ayuda a mantener una buena estructuración del mismo.


## Ciclo de vida de un Thread

El ciclo de vida de un thread en Java se divide en varios estados:

1. New: El thread ha sido creado, pero todavía no ha sido iniciado.

2. Runnable: El thread ha sido iniciado y se encuentra en la cola de listos para ejecutar.

3. Running: El thread está siendo ejecutado por el sistema operativo.

4. Waiting/Blocked: El thread está en espera o bloqueado, ya sea debido a una llamada a un método de espera o debido a la adquisición de un bloqueo.

5. Terminated: El thread ha finalizado su ejecución o ha sido interrumpido.

El cambio entre estados depende de las llamadas a los métodos del thread y de la programación concurrente en el sistema operativo. Por ejemplo, cuando un thread es iniciado con el método start(), pasa del estado new al estado runnable. Luego, el sistema operativo lo selecciona para ejecutar y pasa al estado running. Si el thread realiza una llamada a un método de espera, como sleep() o wait(), pasará al estado waiting/blocked. Finalmente, cuando el thread ha finalizado su ejecución o ha sido interrumpido, pasa al estado terminated.

## Métodos wait(), notify() y notifyAll()

Los métodos `wait()`, `notify()` y `notifyAll()` son métodos de la clase Object que se utilizan para sincronizar la ejecución de los threads en Java. Estos métodos son parte del mecanismo de monitores de Java, que permite controlar el acceso a recursos compartidos entre varios threads.

* El método `wait()` permite que un thread se ponga en espera (waiting) hasta que otro thread lo notifique (notify) o lo despierte (notifyAll). El thread en espera libera el bloqueo del objeto y permite que otros threads accedan al recurso compartido.

* El método `notify()` permite despertar un thread que se encuentra en espera (waiting) sobre el objeto. El thread despertado regresa al estado runnable y puede volver a competir por el acceso al recurso compartido.

* El método `notifyAll()` permite despertar a todos los threads que se encuentran en espera (waiting) sobre el objeto. Todos los threads despertados regresan al estado runnable y pueden volver a competir por el acceso al recurso compartido.

Es importante destacar que estos métodos deben ser utilizados dentro de un bloqueo sincronizado, ya sea mediante un bloqueo explícito o mediante una sentencia synchronized. Esto garantiza que solo un thread puede acceder al recurso compartido a la vez y evita problemas de concurrencia.

## Método sleep()

El método `sleep()` es un método estático de la clase Thread que permite poner a dormir un thread durante un cierto período de tiempo. El método `sleep()` recibe como argumento la cantidad de tiempo en milisegundos que el thread debe dormir.

El método `sleep()` tiene varios usos, como:

* Controlar la velocidad de ejecución de un thread, como en un juego o una animación.

* Simular un proceso que toma cierto tiempo, como una descarga de un archivo o una operación en una base de datos.

* Evitar una sobrecarga de trabajo en un servidor o una aplicación de red.

* Pausar el thread temporalmente durante el debugging o el testing.

Cabe destacar que el método `sleep()` lanza una excepción tipo InterruptedException, si el thread es interrumpido mientras está durmiendo, es importante manejarla.

