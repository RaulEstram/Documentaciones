# Modelo OSI

A pesar de que no se utiliza hoy en dia, se utiliza para enseñar y entender una red.

## Capa de Aplicacion

* Interfaz entre la propia aplicacion y la red
* No sirve a otras capas, solo a la APP
* Provee a la APP un protocolo que le sea Util
    * Navegador WEB - HTTP - GET

## Capa de Presentacion  

* Proporciona a la capa de Aplicacion un formato de datos comun.
* Responsable de la compresion y el cifrado.
* Asegura que la informacion que se envia a la capa de aplicacion se pueda leer.

Podriamos decir que es la capa que define en que idioma se envian los datos.

## Capa de Sesión

* Gestiona las sessiones entre dos host.
* Sincroniza el dialogo entre las capas de presentacion. 
* Administra el intercambio de datos.

## Capa de Transporte

* Establece, mantiene y finaliza las conexiones entre hosts.
* Deteccion y recuperacion de Errores.
* Control de flujo en funcion del rendimiento de la red.

El control de flujo tiene que ver con cuanta informacion se envia en cada momento.

## Capa de Red

* Conectividad entre redes distantes o Distintas.
* Seleccion de ruta - Enrutamiento.
* Direccionamiento Logico.

## Capa de Enlace de Datos

* Acceso a un medio fisico determinado.
* deteccion de errores.
* Direccionamiento Fisico.

## Capa de Fisica

Define las especificaciones Físicas (electricas, codificacion, modulacion de la luz ...) para utilizar el medio físico y enviar las señales que contienen la informacion.

## Equipos que trabajan en cada capa

### Capa 5-7

En las primeras 3 capas superiores que son las capas de aplicacion (Capa 7), presentacion (Capa 6) y sesion (Capa 5) encontraremos equipos como:

* Ordenadores.
* telefonos.
* firewalls.
* servidores. 
* celulares.

> **Warning**
> Esto no quiere decir que solamente trabajan con esas capas, trabajan con esas capas y las inferiores porque si no no podrian enviar y recibir datos.

> **Note**
> Se dice que un equipo es de capa X, cuando trabaja a nivel de esa capa y las capas inferiores.

Protocolos que encontramos en estas capas son:

* HTTP.
* SMTP.
* POP3.
* FTP.

### Capa 4

En la capa de transporte no tiene como tal equipos en especifico o caracteristico de esta capa como en otras capas.

los protocolos de esta capa son:
* TCP.
* UDP.

### Capa 3

En la capa de Red encontramos como equipo estrella al **Router**.

los routers se encargan de interconectar redes distintas y el protocolo principal es el **IP**.

### Capa 2

En la capa de Enlace de datos encontramos como equipo estrella al **Switch**.

QUe da conectividad y aceso a la red a los equipos cableados.

Tambien encontrariamos a los **access point** que ofrecen conectividad pero de forma inalambrica.

El protocolo mas utilizado es el **Ethernet** pero hay muchos otros.

> **Note**
> el tipico modem de internet que tenemos en casa es un todo en uno, ya que hace la funcion de Switch, Router y de Access Point.
> en algunos incluso tiene un firewall que es de las capas superiores

### Capa 1

En esta capa encontraremos equipos como lo son:

* Cables.
* señales de radio.
* Señales opticas.

los estandares que la reculan son:
* Ethernet.
* TIA/EIA 568-B.
* 802.3AN.
* 100BASE-T.


## PDU

En el Modelo TCP/IP el conjunto de datos + cabeceras reciben diferentes nombres dependiendo de la capa como lo son:
* Bits: Capa 1.
* Trama: Capa 2.
* Paquete: Capa 3.
* Segmento: Capa 4.

Pues en el Modelo OSI a esto se le conoce como PDU (Protocol Data Unit) o Unidad de datos de Protocolo y hace referencia a las unidades de datos con las que trabaja cada capa, asi en el modelo OSI los nombres que reciben las PDU's de cada Capa es bastante simple.

| Capas (Modelo Osi) | Modelo TCP/IP | Modelo OSI |
| :-: | :-: | :-: |
| Aplicacion ||L7PDU|
| Presentacion||L6PDU|
Sesión||L5PDU|
|Transporte|Segmento|L4PDU|
|Red| Paquete| L3PDU|
|Enlace de datos | Trama | L2PDU|
| Fisica | Bits | L1PDU| 

> **Note** L por Layer que es capa en español, N numero por el numero de la capa y PDU porque es un PDU. Por lo que la traduccion seria similar a Unidad de Datos de Protocolo de Capa N.

