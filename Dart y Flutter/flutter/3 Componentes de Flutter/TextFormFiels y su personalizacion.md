# TextFormFiels y su personalizacion

El **TextFormField** es un widget que sirve de input en nuestras aplicaciones, el cual tiene una gran interaccion con formularios, es por esto que se recumienda utilizar este y no otros widgets similares.

## Propiedades importantes

En este widget tenemos diferentes propiedades que son importantes y que podremos utilizar frecuentemente como son:
* ```autofocus``` con el cual le decimos si queremos que se le de el focus a un TextFormField por defecto.
* ```initialValue``` le podemos definir un valor inicial al input  
* ```textCapitalization``` podemos definir que vamos a estar capitalizando, por ejemplo **words** para ir capitalizando nombres por ejemplo 
* ```onChanged``` le pasamos una funcion que se va a estar ejecutando cada vez que se realice un cambio en el valor del input.
* ```validator``` y ```validateMode``` son parametros que sirven para validar los datos que se le da a nuestro input

veamos un ejemplo de estas propiedades:

```dart
import 'package:flutter/material.dart';

class InputsScreen extends StatelessWidget {
  const InputsScreen({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: const Text("Diferentes tipos de Inputs"),
        ),
        body: SingleChildScrollView(
          child: Padding(
              padding: const EdgeInsets.symmetric(horizontal: 20, vertical: 10),
              child: Column(
                children: [
                  TextFormField(
                    autofocus: true,
                    initialValue: "",
                    textCapitalization: TextCapitalization.words,
                    onChanged: ((value) {
                      print(value);
                    }),
                    validator: (value) {
                      if (value == "") {
                        return "Necesita un valor";
                      }
                      if (value != null && value.contains("puto")) {
                        return "Oyeme no seas grocero.";
                      }
                      return value != null && value.length < 3
                          ? "Necesita minimo 3 letras"
                          : null;
                    },
                    autovalidateMode: AutovalidateMode.onUserInteraction,
                  )
                ],
              )),
        ));
  }
}
```

## personalizacion

Para personalizar nuestro input tenemos las siguientes opciones:

* ```hintText``` que seria el hover de nuestro input cuando esta seleccionado
* ```labelText``` que sera el titulo de nuestro input y sera el hovver de nuestro input cuando no tiene el focus
* ```helperText``` pequeño texto de ayuda para el usuario en la parte inferior izquierda
* ```counterText``` pequeño texto de ayuda para el usuario en la parte inferior derecha
* ```suffixIcon``` icono para la parte derecha de nuestro input 
* ```prefixIcon``` icono para la parte izquierda de nuestro input
* ```icon``` icono en la parte izquierda d enuestro input, pero este mueve todo el input, no esta dentro de este como los 2 anteriores
* ```border: [OutlineInputBorder]``` sirve para definir el borde de nuestros inputs

un ejemplo seria el siguiente:

```dart
import 'package:flutter/material.dart';

class InputsScreen extends StatelessWidget {
  const InputsScreen({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: const Text("Diferentes tipos de Inputs"),
        ),
        body: SingleChildScrollView(
          child: Padding(
              padding: const EdgeInsets.symmetric(horizontal: 20, vertical: 10),
              child: Column(
                children: [
                  TextFormField(
                      autofocus: false,
                      initialValue: "",
                      textCapitalization: TextCapitalization.words,
                      onChanged: ((value) {
                        print(value);
                      }),
                      validator: (value) {
                        if (value == "") {
                          return "Necesita un valor";
                        }
                        if (value != null && value.contains("puto")) {
                          return "Oyeme no seas grocero.";
                        }
                        return value != null && value.length < 3
                            ? "Necesita minimo 3 letras"
                            : null;
                      },
                      autovalidateMode: AutovalidateMode.onUserInteraction,
                      decoration: const InputDecoration(
                          hintText: "Nombre del usuario",
                          labelText: "Nombre",
                          helperText: "Ingrese el nombre que quiere de usuario",
                          counterText: "De 3 a 12 letras",
                          suffixIcon: Icon(Icons.people),
                          prefixIcon: Icon(Icons.safety_check),
                          icon: Icon(Icons.check),
                          border: OutlineInputBorder(
                              borderRadius: BorderRadius.only(
                                  bottomLeft: Radius.circular(15),
                                  topRight: Radius.circular(15)))))
                ],
              )),
        ));
  }
}

```

## Centralizar estilos del TextFormField

Para centralizar los estilos usaremos nuestro archivo donde tenemos nuestros themas personalizados.

un ejemplo seria la siguiente configuracion de todo un tema:

```dart
import 'package:flutter/material.dart';

class AppTheme {
  static const Color primary = Color.fromRGBO(181, 131, 141, 1);
  static const Color second = Color.fromRGBO(109, 104, 117, 1);

  static final ThemeData lightTheme = ThemeData.light().copyWith(
      primaryColor: primary,
      appBarTheme:
          const AppBarTheme(color: primary, elevation: 0, centerTitle: true),
      textButtonTheme: TextButtonThemeData(
          style: TextButton.styleFrom(
        foregroundColor: second,
      )),
      cardTheme: const CardTheme(elevation: 5),
      floatingActionButtonTheme: const FloatingActionButtonThemeData(
          backgroundColor: second, elevation: 10),
      elevatedButtonTheme: ElevatedButtonThemeData(
          style: ElevatedButton.styleFrom(
        backgroundColor: primary,
        shape: const StadiumBorder(),
      )),
      inputDecorationTheme: const InputDecorationTheme(
        floatingLabelStyle: TextStyle(color: primary),
        focusedBorder: OutlineInputBorder(
            borderSide: BorderSide(color: primary, width: 2),
            borderRadius: BorderRadius.all(Radius.circular(10))),
        enabledBorder: OutlineInputBorder(
            borderSide: BorderSide(color: second, width: 2),
            borderRadius: BorderRadius.all(Radius.circular(10))),
        focusedErrorBorder: OutlineInputBorder(
            borderSide: BorderSide(color: Colors.red, width: 2),
            borderRadius: BorderRadius.all(Radius.circular(10))),
        errorBorder: OutlineInputBorder(
            borderSide: BorderSide(color: Colors.red, width: 2),
            borderRadius: BorderRadius.all(Radius.circular(10))),
        iconColor: primary,
      ));
  static final ThemeData darkTheme = ThemeData.light().copyWith(
      primaryColor: primary,
      appBarTheme: const AppBarTheme(color: primary, elevation: 0));
}
```

## Email, password y diferentes tipos de textFormField 

Para definir el tipo de textFormFiel usaremos la propiedad ```keyboardType```.


## Custom TextFormField

un ejemplo de un TextFormField Custom seria el siguiente:


```dart
import 'package:flutter/material.dart';

class CustomTextFormField extends StatelessWidget {
  final IconData? icono;
  final String? hintText;
  final String? labelText;
  final String? helperText;
  final String? counterText;
  final TextInputType? textInputType;
  final bool? hiddenText;
  final TextCapitalization? textCapitalization;

  const CustomTextFormField({
    Key? key,
    this.icono,
    this.hintText,
    this.labelText,
    this.helperText,
    this.counterText,
    this.textInputType,
    this.hiddenText,
    this.textCapitalization,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return TextFormField(
        keyboardType: textInputType,
        autofocus: false,
        initialValue: "",
        textCapitalization: textCapitalization ?? TextCapitalization.none,
        obscureText: hiddenText ?? false,
        onChanged: ((value) {
          print(value);
        }),
        validator: (value) {
          if (value == "") {
            return "Necesita un valor";
          }
          if (value != null && value.contains("puto")) {
            return "Oyeme no seas grocero.";
          }
          return value != null && value.length < 3
              ? "Necesita minimo 3 letras"
              : null;
        },
        autovalidateMode: AutovalidateMode.onUserInteraction,
        decoration: InputDecoration(
            hintText: hintText,
            labelText: labelText,
            helperText: helperText,
            counterText: counterText,
            icon: icono == null ? null : Icon(icono)));
  }
}
```