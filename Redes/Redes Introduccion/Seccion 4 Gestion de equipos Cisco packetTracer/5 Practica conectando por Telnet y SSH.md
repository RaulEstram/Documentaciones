# Practica: Conectando por Telnet y SSH

Como se vio anteriormente en la Introduccion de esta Seccion, podemos conectarnos al CLI del IOS de un equipo de red Fisicamente, y es lo que hemos hecho en los anteriores 2 Ejercicios Practicos, pero esto no siempre sera posible, es por esto que veremos como conectarnos por Telnet y SSH.

> **Note** : No configuraremos SSH ni Telnet, sólo nos conectaremos utilizando estos protocolos por el momento.

**Para esta practica se utilzara el archivo "4 5 Laboratorio conexion Telnet y SSH.pkt" que se encuentra en la carpeta "Programas".**

Este archivo ya tiene toda la configuracion necesaria para realizar esta practica donde solamente nos vamos a conectar.

## Pasos

### Telnet

Para conectarnos por telnet tenemos que hacer lo siguientes pasos:

* Desde el desktop del portatil seleccionaremos **Command Prompt**.
* Pasaremos el comando ```telnet```y posteriormente la direccion IP del Switch al que nos queremos conectar, que en este caso seria ```>telnet 10.0.0.1```
* ingresamos el usuario y constraseña para conectarnos, en este caso el usuario es "**alumno**" y la contraseña es "**2020**".

Una vez hecho lo anterior veremos que entramos al CLI del equipo en Modo EXEC Usuario. Si queremos ir al Modo EXEC Privilegiado escribimos el comando ```enable``` y nos pedira una contaseña la cual es "**1234**", esto se debe a que Cisco nos obliga a definir una contraseña para acceder al modo privilegiado cuando se utiliza SSH o Telnet.

### SSH

Para conectarnos por SSH tenemos que hacer los siguientes pasos:

* Tenemos que escribir el siguiente comando:
    * ```ssh -l {usuario} {IP}```, en este caso el comando seria ```ssh -l alumno 10.0.0.1```
* escribimos la contraseña que es "**2020**"

Una vez hecho lo anterior podremos entrar al CLI del Switch, y de la misma forma que para Telnet, podemos acceder al modo EXEC Privilegiado usando el comando ```enable``` con la contraseña "**1234**"