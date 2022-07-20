# Funciones del Switch: learning y Forwarding

Hasta ahora hemos dicho que un Switch cuando le llega una Frame o Trama, lo pone en la cola de espera antes de reenviarlo, Posteriormente enviar las tramas por puertos especificos en funcion de la informacion que tenga el switch aprendida sobre la red, podriamos decir que el switch intenta enviar la trama por el puerto que se encuentra el destino en lugar de enviarlos por todos como un HUB

Entonce ahora sabemos que el switch almacena informacion sobre la red para tomar decisiones de envio, y esta informacion la guarda en lo que se llama MAC address table o tabla de direcciones MAC.

## Tabla de direcciones MAC

lo que tiene esta tabla de direcciones MAC en el Switch es asociaciones entre puertos y direcciones mac, por lo que sabe que equipo o quipos tiene conectado a cada puerto.

| Direcion MAC | Puerto |
| :-: | :-: |
| 1111.1111.111| Puerto 10 |
| 2222.2222.2222 | Puerto 16 |
| 3333.3333.3333 | Puerto 13 |
| 4444.4444.4444 | Puerto 32 |



> **Note**
> Recuerda que las direcciones MAC Son las que identifican de forma unica a cada interfaz de red, a cada equipo.

El **Switch entiene de direcciones MAC** que son direcciones de capa 2 por lo que **el Switch se considera de capa 2** a diferencia del HUB que es de capa 1.

## Forwarding 

El Forwarding es el reenvio de tramas de un puerto a otro puerto.

Lo que hace el Switch es lo siguiente:
* 1.- recibe una trama por un puerto, esta trama en su cabecera en la parte destino tendra la direccion MAC destino que es la direccion del equipo que tendra que recibir la informacion.
* 2.- El Swich toma la informacion de la direccion MAC destino y la busca en su tabla de Direcciones MAC y reenvia la trama por el puerto al que esta asociada la direccin MAC destino.

Pero ¿y si la direccion MAC destino no se encuentra en la tabla de direcciones MAC?

El proceso en un principio es el mismo, va a buscar la direccion MAC destino en su tabla de direcciones MAC, pero si llega al final y no la a encontrado entonces reenviara la trama por todos los puertos menos por el que lo ha recibido, de esta forma se asegura de que llegara de una forma u otra.

A esta situacion se le conoce como **Flooding** que en español seria como inundacion pero nos quedaremos con su nombre en ingles, el Flooding reenvia la trama por todos los puertos excepto por el que le ha llegado.

## Learning 

El proceso de Learning es el proceso en el que se construye la tabla de direcciones MAC.

Este proceso es un proceso automatico y consta de lo siguiente:

* Cuando un Switch recibe una trama comprueba si en la tabla de direcciones MAC ya esta la direccion MAC origen.
* En caso de que no exista, entonce ahora sabe que el puerto Fa0/1 tiene x direccion MAC y añade esta informacion a la tabla de direcciones MAC 

## Resumen

En conclusion podemos decir que los Switch tiene 2 funciones principalemente

* **Forwarding**: que es la eleccion de puerto/s por los que reenvia la trama, y para esto utiliza el Destino de la cabecera de la trama.
    * En algunos casos optara por realizar el **Flooding** que es inundar la red con la trama, donde envia la trama por todos los puertos excepto por el de llegado.
* **Learning**: añade las direcciones MAC e interfaz origen a la MAC address Table y para esto utiliza el Origen de la cabecera de la trama.


