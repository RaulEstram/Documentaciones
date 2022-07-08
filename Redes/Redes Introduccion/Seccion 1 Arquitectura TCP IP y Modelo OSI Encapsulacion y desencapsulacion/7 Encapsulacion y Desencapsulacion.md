# Encapsulacion y Desencapsulacion

## Encapsulacion (Envio de datos)

Todo el proceso donde cada capa agrega informacion correspondiente a su protocolo a los datos que recibe de la capa superior se le llama **encapsulacion**.

Esto nos da una idea clara del orden en el que se procesan los datos por parte de la pila TCP/IP.

Cuando hablamos de la pila, hablamos de la pila de protocolos de las diferentes capas y esto es muy util al hacer **troubleshooting** que traducido haria referencia a la resolucion de problemas o incidencias.

# Desencapsulacion (Recepción de Datos)

La recepcion de datos va a empezar de forma contrario al envio de datos, donde recibira 0's y 1's o bits mediante la capa fisica.

Posteriormente pasara a la capa superior que es la capa de enlace de datos, donde es capas de distinguir la cabecera correspondiente de su capa, leera esta informacion para saber que es lo que tiene que hacer, por ejemplo, si se da cuenta que esa informacion no es para su equipo entonces dejaria de procesarla, pero si la direccion destino es la suya entonces, quitara su cabecera y la pasaria a su capa superior.

Este proceso lo harian todas las capas superiores, donde verian que hacer con la informacion recibida, por ejemplo dejar de procesarla, o procesarla donde tendrian que quitar su cabecera correspondiente y la demas informacion pasarla a su capa superior.

Todo este proceso se le conoce como **Desencapslación**


## Resumen

La encapsulacion es el proceso en el que teniendo unos datos recibidos por la capa superior se le añade una cabecera a estos datos y se envia todo junto a la capa superior.

Mientras que la Desencapsulacion es el proceso contrario al recibir unos datos de la capa inferior le quitamos la cabecera de nuestra capa y lo que queda lo pasamos a la capa superior 


![Imagen1]()


hay una terminologia especifica para hacer referencia al conjunto de informacion que recibe o genera cada capa:

* **Segmento**: En la capa de transporte al conjunto de datos + cabecera se le llama **segmento**.

* **Paquete**: En la capa de Red, al conjunto de datos + cabecera se le llama **Paquete**.

* **Trama**: En la capa de Enlace de datos, al conjunto de datos + cabecer se le llama **Trama**.

* **Bits**:  En la capa Fisica, al conjunto informacion que recibe de la capa superior se le llama **bits**.

En ingles se les conoce como:

* Segmento = Packet Segment
* Paquete = Packet
* Trama = Frame
