# Modelos de Red

### ¿Qué es un modelo de red?

Es un conjunto de documentos que definen el funcionameinto de una red.

Desde el año 2000 hasta la actualidad tenemos el modelo TCP/IP.

> **Note**
> las ventajas de utilizar un modelo son:
> * La Estandarización
> * La Compatibilidad
> * La Modularidad

## Modelo TCP/IP Original

### ¿Qué es el modelo TCP/IP?

Es un conjunto de protocolos que permiten la comunciación entre dispositivos.

Esos protocolos estan definidos en documentos.

Los documentos para el modelo TCP/IP se llaman RFC (Rquest For Comments) y los administra el IETF (Internet Engineering Task Force).

### Modelo TCP/IP

Este Modelo TCP/IP Se trata de un conjunto de protocolos, pero no solamente tenemos protocolos, si no que segmentamos el modelo en diferentes capas dependiendo de la funcion de cada protocolo.

Las capas de Modelo TCP/IP son:
* Capa de Aplicacion
* Capa de Transporte
* Capa de Internet
* Capa de Enlace

Los modelos en general segmentan las funciones y las agrupan en capas. Las capas superiores se centran mas en la parte de la aplicacion que requiere enviar o recibir datos, mientras que las capas inferiores se centran mas en la parte del envio de la informacion en el medio fisico.
La capa del medio tambien conocida como capa de internet o de red se ocupa de que la informacion enviada en un origen llegue a su destino, en otras palabras se encarga de todo el transito en la red.

## Modelo OSI

El modelo OSI tiene las siguientes capas:

* Capa de Aplicacion
* Capa de Presentacion
* Capa de Sesión
* Capa de Transporte
* Capa de Red
* Capa de Enlace de datos
* Capa de Fisica


A pesar de que el Modelo TCP/IP termino siendo el que se impuso ante los demas modelos, esto no quiere decir que el modelo OSI murio, este modelo termino siendo relegado al mundo academico ya que se utiliza mucho a nivel de terminologia tecnica.

Como se segmenta mucho mas este modelo facilita la comprencion a mas detalle.

Es por esto que todavia se utiliza terminologia tecnica en terminos del Modelo OSI, por ejemplo:

* Switch de capa 2, de la capa 2 del modelo OSI que es la capa de Enlace de datos.
* Switch de capa 3, de la capa 3 del modelo OSI que es la capa de Red



## Capas de los diferenes Modelos

Vista general a las capas de los modelos TCP/IP y OSI

<table>
    <thead>
        <tr>
            <th>Modelo Osi</th>
            <th>Modelo TCP/IP Original</th>
            <th>Modelo TCP/IP actual</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Aplicación</td>
            <td rowspan=3>Aplicación</td>
            <td rowspan=3>Aplicación</td>
        </tr>
        <tr>
            <td> Presentación </td>
        </tr>
        <tr>
            <td> Sesión </td>
        </tr>
        <tr>
            <td>Transporte</td>
            <td>Transporte</td>
            <td>Transporte</td>
        </tr>
        <tr>
            <td>Red</td>
            <td>Internet</td>
            <td>Red</td>
        </tr>
        <tr>
            <td>Enlace de datos</td>
            <td rowspan=2>Enlace</td>
            <td>Enlace de datos</td>
        </tr>
        <tr>
            <td>Fisica</td>
            <td>Fisica</td>
        </tr>
    </tbody>
</table>


> **Note**
> capa en ingles es Layer
> Entonces podriamos decir cosas como:
> * Layer 3 Switch
> * Layer 3 = L3