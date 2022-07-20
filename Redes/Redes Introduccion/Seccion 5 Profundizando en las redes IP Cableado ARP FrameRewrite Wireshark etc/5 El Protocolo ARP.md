# Protocolo ARP

Cuando tenemos que enviar informacion de un equipo a otro equipo de la misma Red por ejemplo, las cabeceras de capa 3 tendran el IP origen y el IP destino los cuales no son ningun problema, por otro lado, las cabeceras de capa 2 tendran la direccion MAC origen el cual tampoco es un problema, pero debera de tener la direccion MAC destino el cual si puede ser un problema porque se desconoce, es aqui donde entra **el protocolo ARP que nos permitira descubrir la direccion MAC de otro equipo del que solo disponemos su IP**.

El protocolo ARP (Address Resolution Protocol o Protocolo de Resolucion de Direcciones) es un Protocolo de capa 2, por lo que va encapsulado dentro de la cebecera de esta capa.

## Funcionamiento del Protocolo ARP

Para saber el funcionamiento de este protocolo imaginemos que tenemos la siguiente Red:

![Imagen29]()

Si el PC1 con IP 30.0.0.50 le quiere mandar informacion o un ping al PC4 con IP 30.0.0.53 pero le falta la direccion MAC del PC4 entonces se realizaran los siguientes pasos:

- El PC1 generara una Trama ARP con MAC destino **ffff.ffff.ffff**
- De esta forma hacemos que esta Trama le llegue a todos los Equipos de la Red.
- La trama para darnos una idea contiene la pregunta **¿Que MAC tiene la IP 30.0.0.53?**.
- Los equipos que no sean el PC4 con IP 30.0.0.53 descartaran la Trama porque no es su IP.
- El PC4 con IP 30.0.0.53 al ver que si es su IP, respondera con su MAC y esta respuesta sera de tipo Unicast.
- Una vez que el PC1 con IP 30.0.0.50 obtenga la respuesta, guardara la direccion MAC del PC4 con IP 30.0.0.53 en una tabla llamada **Tabla ARP**.
- Finalmente el PC1 podra enviar la informacion o el ping al PC4.

> **Nota** Cuando la direccion MAC destino es **ffff.ffff.ffff** nos referimos a la direccion de Broadcast, lo cual significa que se lo enviara a todos los equipos.

> **Note** las tablas ARP son un conjunto de asociaciones entre direcciones IP y Direcciones MAC.

Por lo tanto el protocolo ARP consta de **2 Fases**:

- Peticion ARP
- Respuesta ARP

Lo unico que hacen estas 2 fases es enviar Tramas

## Informacion del Protocolo ARP

La informacion propia del Protocolo ARP estara en el capo Datos de la una Trama Ethernet y va a tener la siguiente estructura:


---

<table align="center">
	<tbody>
		<tr>
			<td colspan="1" style="text-align:center">Cell 1x1</td>
		</tr>
		<tr>
			<td colspan="2">Cell 1x2</td>
			<td colspan="2">Cell 2x2</td>
		</tr>
		<tr>
			<td>Cell 1x3</td>
			<td>Cell 2x3</td>
			<td>Cell 3x3</td>
			<td>Cell 4x3</td>
		</tr>
		<tr>
			<td>Cell 1x4</td>
			<td>Cell 2x4</td>
			<td>Cell 3x4</td>
			<td>Cell 4x4</td>
		</tr>
		<tr>
			<td>Cell 1x5</td>
			<td>Cell 2x5</td>
			<td>Cell 3x5</td>
			<td>Cell 4x5</td>
		</tr>
		<tr>
			<td>Cell 1x6</td>
			<td>Cell 2x6</td>
			<td>Cell 3x6</td>
			<td>Cell 4x6</td>
		</tr>
	</tbody>
</table>

---

<table class="tftable" border="1">
<tr>
    <th colspan="4">Estructura del Protocolo ARP</th>
</tr>

<tr>
<td colspan="2">HARDWARE TYPE</td>
<td colspan="2">PROTOCOL TYPE</td>
</tr>
<tr>
<td colspan="1">HARDWARE ADDRESS LENGTH</td>
<td colspan="1">PROTOCOL ADDRESS LENGHT</td>
<td colspan="2">OPERACION CODE</td>
</tr>
<tr>
<td colspan="4">SENDER HARDWARE ADDRESS</td>
</tr>
<tr>
<td colspan="4">SENDER PROTOCOL ADDRESS</td>
</tr>
<tr>
<td colspan="4">TARGET HARDWARE ADDRESS</td>
</tr>
<tr>
<td colspan="4">TARGET PROTOCOLO ADDRESS</td>
</tr>
</table>
