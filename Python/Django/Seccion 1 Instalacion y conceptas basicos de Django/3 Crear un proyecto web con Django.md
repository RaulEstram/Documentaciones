# crear un proyecto web con Django

## Pasos

### 1° Paso - Creacion y activacion de un entorno virtual

la primero que tenemos que hacer es crear y activar un entorno virtual.

```
$ source /.../activate
```

### 2° Paso - Creacion del proyecto 

Tenemos que ubicarnos en nuestra carpeta donde estara nuestro proyecto.

Una ves posicionados en la carpeta procederemos a usar el siguiente comando:

Linux & Windows

```bash
$ django-admin startproject {Nombre proyecto}
```

por ejemplo


```bash
$ django-admin startproject prueba1
```

> **Note** Una vez hecho esto se crearan varios archivos que se veran posteriormente

### 3° Paso - Comprobacion del proyecto o ejecutar el proyecto

Para verificar que el proyecto se crea adecuadamente o para simplemente ejecutar el proyecto tendremos que posicionarnos donde se crearon los archivos en el paso anterior y ejecutar el siguiente comando: 

Linux

```bash
python manage.py runserver
```

Windows

```bash
py manage.py runserver
```

Una vez ejecutado el comando te marcara o te dira que se desplejo tu proyecto y te dara una direccion en la que puedes ingresar para ver tu proyecto similar a la siguiente: http://127.0.0.1:8000/

Entrando a esta direccion podremos ver nuestro proyecto desplejado o en ejecucion 

![Imagen 1](https://github.com/RaulEstram/Documentaciones/blob/main/Python/Django/Imagenes/Imagen1.png)
