# Imagenes

Hay diferentes formas de agregar imágenes a nuestras aplicaciones. Ya sea que estas sean de internet o estén incluidas en nuestras aplicaciones.

En esta caso vamos a ver las 2 formas.


## Imagenes en internet

Para agregar imágenes usaremos la siguiente sintaxis:

```dart
Image(image: NetworkImage("url_imagen_internet")),
```


## pasos para usar imagenes estaticas de nuestra aplicacion

Para realizar esta esta tarea es muy importante seguir los siguientes pasos:

* Tenemos que crear una carpeta llamada ```assets``` en la raíz del proyecto (afuera de nuestra carpeta lib) en donde agregaremos toda la multimedia como pueden ser imágenes o gifs.

* editaremos el archivo ```pubspec.yaml```.

    * En la sección de ```flutter``` encontraremos comentado una sub sección llamada ```assets:```, tenemos que des comentarla.

    * Después, como lo muestran los ejemplos, tenemos que agregar las rutas de nuestros archivos estáticos.

Veamos un ejemplo de como quedaría nuestro archivo ```pubspec.yaml```:

```dart
 The following section is specific to Flutter packages.
flutter:

  # The following line ensures that the Material Icons font is
  # included with your application, so that you can use the icons in
  # the material Icons class.
  uses-material-design: true

  # To add assets to your application, add an assets section, like this:
  assets:
    - assets/
  #   - images/a_dot_ham.jpeg
```


## Imagenes de nuestra aplicacion

Para agregar imágenes que esten en nuestra aplicacion usaremos la siguiente sintaxis:

```dart
Image(image: AssetImage('assets/imagen_estatica.gif'))
```

## imagenes de internet con un loading.

Para que nuestras imágenes tengan un loading mientras se cargan usaremos la siguiente sintaxis:

```dart
FadeInImage(placeholder: AssetImage("assets/imagen_para_el_loaging.gif"), image: NetworkImage("url imagen de internet"))
```


## Ajustar el tamaño de la imagen y otras cosas.

### dentro del widget de Image o FadeInImage

para ajustar los tamaños de las imagenes usaremos las siguientes propiedades:

* width: ancho
* height: largo
* fit
* fadeInDuration: furacion en revelar la imagen en FadeInImage

Lo recomendado es que se utilicen los siguientes valores:

* width: double.infinity
* fit: BoxFit.cover

Para que el ancho de la imagen, se adapte al contenedor y tenga un fit cover, que hace que la imagen tambien se adapte de buena manera sin que se vea muy afectada.

Por otro lado el **heigt** es al gusto al igual de la duracion con fadeInDuration.

Un ejemplo seria el siguiente:

```dart
FadeInImage(
  placeholder: AssetImage("assets/loagingGif.gif"),
  image: NetworkImage("https://images.alphacoders.com/906/906972.png"),
  width: double.infinity,
  height: 230,
  fit: BoxFit.cover,
  fadeInDuration: Duration(milliseconds: 300),
)
```
