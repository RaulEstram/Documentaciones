# Protocolo ICMP y ping

ICMP (Internet Control Message Protocol o protocolo de mensajes de control de internet) es un protocolo de control y notificacion de errores, sus principales funciones son:

* Diagnostico
* notificacion

Un ejemplo es la herramienta **ping** que se basa en el protocolo ICMP ya que usa este para realizar su funcionalidad que es comprobar la conectividad entre dos equipos lo que nos permite saber que hay una adecuada comunicacion.

## Protocolo ICMP

Este protocolo funciona sobre el protocolo IP, en otras palabras que ira encapsulado dentro del protocolo IP, es decir que la informacion ICMP estara dentro de los datos del paquete.

La informacion ICMP constara de una cabecera y unos datos, la cabecera tendra por lo menos 4 bytes donde:

* 1 byte para el campo **Type**
* 1 byte para el campo **Code**
* 2 bytes para el campo **Checksum**

El resto de la cabecera depende del tipo de mensaje ICMP y los datos seran opcionales, a pesar de esto hay 2 campos que tambien se veran constantemente que son:

* identifier
* Squence Number

Estos 2 campos en pocas palabras nos ayudan para saber que una comunicacion completa por medio del **ping** se hizo adecuadamente ya que el mensaje y la respuesta tienen que tener el mismo **identifier** y el mismo **sequence number** number para saber que todo esta bien y que no hay ningun problema, estos campos lo encontraremos principalmente cuando el tipo del mensaje ICMP sea 8 o 0.

Este protocolo se puede considerar de capa 4 o capa de Transporte ya que es un protocolo que se encapsula sobre el protocolo IP pero al mismo tiempo tambien se considera como un subprotocolo del protocolo IP por lo que se puede considerar un protocolo de la capa 3 o capa de red, aunque generalmente se le considera de la capa 3 por la gran mayoria.

> **Note** para encontrar mas informacion para saber que significa cada tipo y codigo de un ICMP podemos buscarlo en la pagina de [iana - Internet Control Message Protocol (ICMP) Parameters](https://www.iana.org/assignments/icmp-parameters/icmp-parameters.xml)

## Ping

El ping es una herramienta que permite comprobar la conectividad a nivel 3 y corre sobre el protocolo IP.

El ping utiliza el protocolo ICMP en dos tipos diferentes que serian:

* ICMP - Echo Request - Este sera el tipo de mensaje ICMP que utilizara el equipo que manda el ping.

* ICMP - Echo Reply - Este sera el tipo de mensaje ICMP que utilizara el equipo que manda la respuesta.

