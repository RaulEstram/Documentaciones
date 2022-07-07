# Entornos virtuales

Hay muchas formas de crear entornos virtuales en python, pero en este caso vamos a ver como realizar entornos virtuales con **virtualenv**.

## Pasos

### Antes que nada

Antes que nada tenemos que asegurarnos de tener una carpeta donde estaremos poniendo o guardando nuestros entornos vituales.

---

### 1° Paso (Crear entorno virtual)

Desde la terminal, tenemos que posicionarnos en la carpeta de nuestros entornos virtuales y utilizar el siguiente comando

* Lunux

```bash
$ python3 -m venv {Nombre del Entorno Virtual}
```

* Windows

```bash
$ python -m venv {Nombre del Entorno Virtual}
```

> **Note**
> Puede que en linux te pida instalar alguna cosa, en dicho caso hay que instalarla, dicha instalacion sera similar a: ```sudo apt install python3.N-venv```

Una vez hecho esto ya tendremos nuestro entorno virtual.

---

### 2° Paso (Activar o utilizar el entorno virtual)

Una vez creado nuestro entorno virtual tenemos que activarlo o indicarle al sistema operativo que entorno estara en curso para esto tendremos que realizar los siguientes pasos:

#### Windows

* Entramos a la **carpeta del entorno virtual**
* Entramos a la **Subcarpeta llamada Scripts**
* Ejecutamos el **archivo activate**

o simplemente ejecutamos el archivo usando una ruta relativa o absoluta

Para saber que lo estamos utilizando en nuestra terminal aparecera un parentesis antes del path de nuestra ubicacion con el nombre del entorno virtual

#### Linux

* Entramos a la **carpeta del entorno virtual**
* Entramos a la **Subcarpeta llamada Bin**
* Ejecutamos el comando ```source activate```

Para saber que lo estamos utilizando en nuestra terminal aparecera un parentesis antes del path de nuestra ubicacion con el nombre del entorno virtual

Tamien podemos usar el comando ```which python``` o ```which python3``` y nos dira que entorno de python esta ejecutando, por defecto estara usando un python instalado en alguna otra parte como es /usr/bin/python3

---

### 3° paso (Instalar paquetes en el entorno virtual)

En este punto que ya creamos nuestro entorno virtual y lo activamos podemos empezar a instalar paquetes en nuestro nuevo entorno virtual usando **pip**, en este caso instalaremos django usando el siguiente comando:

```bash
$ pip install django
```

o 

```bash
$ pip3 install django
```

> **Warning**
> Es muy importante que el entorno virtual este activado.

> **Note**
> para ver que paquetes o modulos tenemos instalados en nuestro entorno virtual podemos usar alguno de los siguientes comando: ```pip list```, ```pip3 list```, ```pip freeze``` o ```pip freeze local```.