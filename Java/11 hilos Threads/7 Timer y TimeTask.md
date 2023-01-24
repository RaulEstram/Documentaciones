# Timer y TimerTask

**Timer** y **TimerTask** son dos clases en Java que se utilizan para programar tareas para su ejecución en un momento futuro.

La clase **Timer** es una clase que permite programar tareas para su ejecución en un momento específico o después de un retraso determinado. Puedes crear una instancia de **Timer** y luego programar una tarea para su ejecución en un momento específico o después de un retraso utilizando el método schedule().

La clase **TimerTask** es una clase abstracta que representa una tarea a ser programada. Para programar una tarea, debes crear una clase que herede de **TimerTask** y sobreescribir su método run(). La tarea se programa utilizando un objeto Timer.

Un ejemplo de uso de **Timer** y **TimerTask** sería programar una tarea para que se ejecute cada cierto tiempo, por ejemplo, cada 10 segundos, para actualizar una base de datos o para realizar una tarea específica.

## Ejemplo de uso de Time y TimerTask

```java
package ejemplotimer;

import java.awt.*;
import java.io.IOException;
import java.util.Date;
import java.util.Timer;
import java.util.TimerTask;
import java.util.concurrent.atomic.AtomicInteger;

public class EjemploTimer {
    public static void main(String[] args) {
        Timer timer = new Timer();
        // se repite una sola vez
        timer.schedule(new TimerTask() {
            @Override
            public void run() {
                System.out.println("Inicio ejecución de la tarea.");
                System.out.println("Fin ejecución de la tarea.");

            }
        }, 3000);

        // se repite constantemente
        timer.schedule(new TimerTask() {

            private int cantidad;

            @Override
            public void run() {
                cantidad++;
                System.out.println("Inicio ejecución de la tarea repetitiva.");
                System.out.println("Fin ejecución de la tarea repetitiva.");

                if (cantidad > 5){
                    timer.cancel();
                }
            }
        }, 3000, 10000);


        // se repite constantemente y con control de variables fuera de la clase
        // usando AtomicType
        AtomicInteger contadorEjecuciones = new AtomicInteger();
        timer.schedule(new TimerTask() {
            @Override
            public void run() {
                contadorEjecuciones.incrementAndGet();
                if (contadorEjecuciones.get() >= 10) timer.cancel();


                System.out.println("contadorEjecuciones = " + contadorEjecuciones);
                System.out.println(new Date());
                Toolkit toolkit = Toolkit.getDefaultToolkit();
                toolkit.beep();
                try {
                    Runtime.getRuntime().exec("paplay /usr/share/sounds/freedesktop/stereo/bell.oga ");
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }

            }
        }, 0, 1000 );

    }
}

```