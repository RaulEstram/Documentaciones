# Protocolo ARP

Cuando tenemos que enviar informacion de un equipo a otro equipo de la misma Red por ejemplo, las cabeceras de capa 3 tendran el IP origen y el IP destino los cuales no son ningun problema, por otro lado, las cabeceras de capa 2 tendran la direccion MAC origen el cual tampoco es un problema, pero debera de tener la direccion MAC destino el cual si puede ser un problema porque se desconoce, es aqui donde entra **el protocolo ARP que nos permitira descubrir la direccion MAC de otro equipo del que solo disponemos su IP**.

El protocolo ARP (Address Resolution Protocol o Protocolo de Resolucion de Direcciones) es un Protocolo de capa 2, por lo que va encapsulado dentro de la cebecera de esta capa.

## Funcionamiento del Protocolo ARP

Para saber el funcionamiento de este protocolo imaginemos que tenemos la siguiente Red:

![Imagen29](https://github.com/RaulEstram/Documentaciones/blob/main/Redes/Redes%20Introduccion/Imagenes/Imagen29.png)

Si el PC1 con IP 30.0.0.50 le quiere mandar informacion o un ping al PC4 con IP 30.0.0.53 pero le falta la direccion MAC del PC4 entonces se realizaran los siguientes pasos:

- El PC1 generara una Trama ARP con MAC destino **ffff.ffff.ffff**
- De esta forma hacemos que esta Trama le llegue a todos los Equipos de la Red.
- La trama para darnos una idea contiene la pregunta **¿Que MAC tiene la IP 30.0.0.53?**.
- Los equipos que no sean el PC4 con IP 30.0.0.53 descartaran la Trama porque no es su IP.
- El PC4 con IP 30.0.0.53 al ver que si es su IP, respondera con su MAC y esta respuesta sera de tipo Unicast.
- Una vez que el PC1 con IP 30.0.0.50 obtenga la respuesta, guardara la direccion MAC del PC4 con IP 30.0.0.53 en una tabla llamada **Tabla ARP**.
- Finalmente el PC1 podra enviar la informacion o el ping al PC4.

> **Nota** Cuando la direccion MAC destino es **ffff.ffff.ffff** nos referimos a la direccion de Broadcast, lo cual significa que se lo enviara a todos los equipos.

> **Note** las tablas ARP son un conjunto de asociaciones entre direcciones IP y Direcciones MAC y podemos verlas usando el comando ```arp -a``` desde el command Prompt de un equipo.

Por lo tanto el protocolo ARP consta de **2 Fases**:

- Peticion ARP
- Respuesta ARP

Lo unico que hacen estas 2 fases es enviar Tramas

## Informacion del Protocolo ARP

La informacion propia del Protocolo ARP estara en el capo Datos de la una Trama Ethernet y va a tener la siguiente estructura:

<table align="center" border="1" style="text-align:center">
	<tbody>
		<tr>
			<td colspan="34">Estructura del Protocolo ARP</td>
		</tr>
		<tr>
			<td colspan="2">Hardware Type</td>
			<td colspan="2">Protocol Type</td>
		</tr>
		<tr>
			<td colspan="1">Hardware Address length</td>
			<td colspan="1">Protocol Address length</td>
			<td colspan="2">Operation Code</td>
		</tr>
		<tr>
			<td colspan="4">Sender Hardware Address</td>
		</tr>
		<tr>
			<td colspan="4"> Sender Protocol Address</td>
		</tr>
		<tr>
			<td colspan="4">Target Hardware Address</td>
		</tr>
        <tr>
			<td colspan="4">Target Protocol Address</td>
		</tr>
	</tbody>
</table>

* Hardware Type = Protocolo de Capa 2, por ejemplo Ethernet.
* Protocol Type = Protocolo de Capa 3, por ejemplo IPv4.
* Hardware Address length y Protocol Address length = se definen los tamaños de un protocolo y del otro, por ejemplo Tamaño direcciones MAC e IP con 6 bytes y 4 bytes.
* Operation Code = Solo puede tomar 2 valores, 1 para peticion ARP o 2 para Respuesta ARP.
* Sender Hardware Address y Sender Protocol Address = Sender -> Remitente/transmisor; contendran la direccion MAC en Hardware y la direccion IP en Protocol del equipo que manda este ARP.
* Target Hardware Address y Target Protocol Address = Target -> Objetivo; ontendran la direccion MAC en Hardware y la direccion IP en Protocol del equipo destino.

> **Note** cuando se envie una peticion ARP el Targen Hardware Address como no la sabemos tendra el valor de 0000.0000.0000
