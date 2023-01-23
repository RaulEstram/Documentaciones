# Métodos join vs Sleep

La diferencia principal entre el método `join()` y el método `sleep()` en Java es que el método `join()` se utiliza para esperar a que un thread específico termine su ejecución, mientras que el método `sleep()` se utiliza para pausar un thread durante un cierto período de tiempo.

* El método `join()` se utiliza para esperar a que un thread específico termine su ejecución antes de continuar con la ejecución del thread que llama a `join()`. Por ejemplo, si un thread A llama al método `join()` en otro thread B, el thread A se bloqueará hasta que el thread B haya finalizado su ejecución.

* El método `sleep()` se utiliza para pausar un thread durante un cierto período de tiempo. El thread que llama al método `sleep()` se detiene temporalmente y no realiza ninguna acción durante el tiempo especificado. El método `sleep()` puede ser utilizado para controlar la velocidad de ejecución de un thread, simular un proceso que toma cierto tiempo, evitar una sobrecarga de trabajo, entre otros usos.

> En pocas palabras, el join nos sirve para esperar a que un hilo que creamos se termine de ejecutar para que se siga ejecutando el hilo donde se llamo, mientras que el sleep simplemente lo detiene y se sigue ejecutanto el hilo dende se llamo.

