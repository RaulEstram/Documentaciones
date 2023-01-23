# Implementando hilos con lambda y Runnable

## Clases anónimas

```java
public class Main {

    public static void main(String[] args) throws InterruptedException {

        // implementation al vuelo o anónima
        Runnable viaje = new Runnable() {
            @Override
            public void run() {

                System.out.println("Se inicia el método run del hilo: " + Thread.currentThread().getName());

                for (int i = 0; i < 3; i++) {
                    try {
                        Thread.sleep(10);
                        System.out.println(Thread.currentThread().getName());
                    } catch (InterruptedException e) {
                        throw new RuntimeException(e);
                    }
                }

                System.out.println("Se finalizo el hilo: " + Thread.currentThread().getName());

            }
        };

        new Thread(viaje, "hilo1").start();
        
    }
}
```

## Lambda GOD

```java
public class Main {

    public static void main(String[] args) throws InterruptedException {

        // implementation al vuelo o anónima
        Runnable viaje = () -> {

            System.out.println("Se inicia el método run del hilo: " + Thread.currentThread().getName());

            for (int i = 0; i < 3; i++) {
                try {
                    Thread.sleep(10);
                    System.out.println(Thread.currentThread().getName());
                } catch (InterruptedException e) {
                    throw new RuntimeException(e);
                }
            }

            System.out.println("Se finalizo el hilo: " + Thread.currentThread().getName());

        };

        new Thread(viaje, "hilo1").start();

    }
}  
```
