# Organizar el archivo Settings.py

Como se menciona con anterioridad el archivo **settings.py** es el archivo en el que se definen las configuraciones de nuestro poryecto y a medida de que nuestro proyecto va creciendo este se puede hacer muy grande lo cual al momento de estar en produccion, en servidor o en desarrollo sea necesario estar realizando varias modificaciones en este archivo, es por esto que vamos a ver como administrarlo o configurarlo de una forma mas profecional para que pueda ser legible, ordenado y adaptarse mas facil.

Para realizar esto tendremos que **dividir** este archivo **setting.py** en **3 partes** las cuales seran:
* un archivo para el entorno local.
* un archivo para el entorno de produccion.
* un archivo que tendra las configuraciones basicas que heredan tanto el entorno local como un entorno de produccion.

## Pasos Para organizar la configuracion de forma profesional

Veremos como son los pasos para empezar a organizar la configuracion de nuestro proyecto para tenerlo de una forma mas escalable y organizada.

---

### Creacion de Archivos y carpeta.

Lo primero que tendremos que hacer es crear una nueva carpeta al mismo nivel del archivo settings.py con el nombre **settings** donde estaran los archivos de nuestra configuracion.

Dentro de esta carpeta agregaremos los archivos:

* **base.py** = aqui tendremos las configuraciones basicas o que las otras 2 configuraciones tendran en comun.
* **local.py** = aqui tendremos las configuraciones para cuando estemos trabajando en un entorno local
* **prod.py** = aqui tendremos las configuraciones para resolvecuando nuestro proyecto este en alojado en un servidor.


Tambien para decirle a django que dentro de una carpeta hay codigo que tiene que leer tenemos que crear dentro de esta carpeta un archivo llamado **"__init__.py"**.

---

### llenado de configuracion inicial.

Tenemos que empezar a llenar los archivos creados con la configuracion inicial que nos proporciona Django por defecto.

#### Base.py

Para el archivo **base.py** pondremos toda la configuracion inicial que tenemos en el archivo **settings.py** que genera Django y eliminaremos las cosas que no vamos a necesitar como comentarios inecesarios o configuracion que no sea general para el entorno local y de produccion como puede ser la configuracion de la base de datos, el debug mode o de Static files.

Una vez que nos quedemos con la configuracion necesaria para el archivo **base.py** nos quedaremos con un codigo similar al siguiente:

* base.py

```python
"""
"""

from pathlib import Path

# Build paths inside the project like this: BASE_DIR / 'subdir'.
BASE_DIR = Path(__file__).resolve().parent.parent

# Quick-start development settings - unsuitable for production
# See https://docs.djangoproject.com/en/4.0/howto/deployment/checklist/

# SECURITY WARNING: keep the secret key used in production secret!
SECRET_KEY = 'django-insecure-z&l7q2gf082+ai)yvd_(bh&kwsbu5@3n)buqz*@qyv!95=*=hi'

# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]

MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'proyectoEmpleados.urls'

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

WSGI_APPLICATION = 'proyectoEmpleados.wsgi.application'

# Password validation
# https://docs.djangoproject.com/en/4.0/ref/settings/#auth-password-validators

AUTH_PASSWORD_VALIDATORS = [
    {
        'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator',
    },
]

# Internationalization
# https://docs.djangoproject.com/en/4.0/topics/i18n/

LANGUAGE_CODE = 'es-mx'

TIME_ZONE = 'UTC'

USE_I18N = True

USE_TZ = True

# Default primary key field type
# https://docs.djangoproject.com/en/4.0/ref/settings/#default-auto-field

DEFAULT_AUTO_FIELD = 'django.db.models.BigAutoField'

```

#### local.py

Por otra parte para el archivo **local.py** pondremos la otra configuracion que estaba en el archivo **settings.py** pero que no la dejamos en el archivo **base.py** como es la configuracion de la base de datos.

Una vez hecho lo anterior nos quedara un codigo similar al siguiente:

* local.py 

```python
"""
"""

from .base import *
from pathlib import Path

# Build paths inside the project like this: BASE_DIR / 'subdir'.
BASE_DIR = Path(__file__).resolve().parent.parent

# SECURITY WARNING: don't run with debug turned on in production!
DEBUG = True

ALLOWED_HOSTS = []

# Database
# https://docs.djangoproject.com/en/4.0/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}

# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/4.0/howto/static-files/

STATIC_URL = 'static/'

```

---

### Levantar proyecto con la nueva configuracion

Una vez que tenemos nuestra configuracion basica hecha mediante nuevos archivos podemos proceder a ejecutar o levantar nuestro proyecto para esto tenemos que activar nuestro entorno virtual para nuestro proyecto y por ultimo ejecutar el siguiente comando:

```bash
$ python manage.py runserver --settings={direccion de la configuracion usando puntos en lugar de diagonales}
```

Un ejemplo seria:

```bash
$ python manage.py runserver --settings=proyectoEmpleados.settings.local
```

Esto teniendo en cuenta que nos encontramos al mismo nivel que el archivo manage.py