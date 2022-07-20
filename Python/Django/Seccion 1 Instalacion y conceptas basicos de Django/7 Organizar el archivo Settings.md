# Organizar el archivo Settings.py

Como se menciona con anterioridad el archivo **settings.py** es el archivo en el que se definen las configuraciones de nuestro poryecto y a medida de que nuestro proyecto va creciendo este se puede hacer muy grande lo cual al momento de estar en produccion, en servidor o en desarrollo sea necesario estar realizando varias modificaciones en este archivo, es por esto que vamos a ver como administrarlo o configurarlo de una forma mas profecional para que pueda ser legible, ordenado y adaptarse mas facil.

Para realizar esto tendremos que **dividir** este archivo **setting.py** en **3 partes** las cuales seran:
* un archivo para el entorno local.
* un archivo para el entorno de produccion.
* un archivo que tendra las configuraciones basicas que heredan tanto el entorno local como un entorno de produccion.