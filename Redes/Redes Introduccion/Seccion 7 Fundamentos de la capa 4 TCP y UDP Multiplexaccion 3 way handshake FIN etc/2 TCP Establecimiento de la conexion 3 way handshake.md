# TCP:  Establecimiento de la conexion. 3-way-handshake

Una de las funcionalidades del protocolo TCP es la conexión que se encarta del establecimiento y del Finalizado, en otras palabras el protocolo TCP Genera y crea conexiones, las establece, las finaliza y las gestiona. 

Una comunicacion TCP la podemos dividir en 3 etapas:
* Establecimiento
* Envio de datos
* finalizado o cierre

## Establecimiento 

El establecimiento de una comunicacion TCP tambien se le conoce como 3-way-handshake el cual:

* Es necesario antes de empezar cualquier envio de datos TCP
* Permite la sincronizacion entre ambos miembros
* crea la conexion entre SOCKETS - Apertura de puertos
* Usa Num SEQ y Num ACK
* Usa FLAGS de control, tambien llamados BITS DE CONTROL / FLAG BITS