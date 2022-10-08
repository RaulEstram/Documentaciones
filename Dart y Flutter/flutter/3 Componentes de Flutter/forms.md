# Forms

Para el uso de forms tenemos que hacer varias cosas y tenemos que tener varios elementos tambien.

## Cosas que hacer

Las cosas que tenemos que hacer son:

* 1.- tenemos que envolver el widget que contiene nuestros TextFormField en un widget llamado **Form**
* 2.- Agregar una variable que servira de nuestro **key** y otra para almacenar la informacion.
* 3.- Editaremos nuestros curtomTextFormField para que resivan como argumento el nombre de una propiedad y en donde almacenaran el valor de esta propiedad (se guardaran en la variable del punto 2)

### CustomTextFormField

para asegurarnos que se cumpla el punto 3 tenemos como ejemplo el siguiente codigo:

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
  // parte del punto 3
  final String formProperty;
  final Map<String, dynamic> formValues;

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
    // parte del punto 3
    required this.formProperty,
    required this.formValues,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return TextFormField(
        keyboardType: textInputType,
        autofocus: false,
        initialValue: "",
        textCapitalization: textCapitalization ?? TextCapitalization.none,
        obscureText: hiddenText ?? false,
        // parte del punto 3
        onChanged: (value) => formValues[formProperty] = value,
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

> **Note** podemos ver como en la propiedad onChanged vamos cambiando el valor que se guarda en la variable que le pasaremos para almacenar la informacion.

### form y variable key

Para los puntos 1 y 2 tenemos el siguiente ejemplo de codigo:

```dart
import 'package:flutter/material.dart';

import '../widgets/widgets.dart';

class InputsScreen extends StatelessWidget {
  const InputsScreen({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    // parte del punto 2 - key
    final GlobalKey<FormState> myFormkey = GlobalKey<FormState>();
    // parte del punto 2 - variable para almacenar informacion
    final Map<String, dynamic> formData = {};

    return Scaffold(
        appBar: AppBar(
          title: const Text("Diferentes tipos de Inputs"),
        ),
        body: SingleChildScrollView(
          child: Padding(
              padding: const EdgeInsets.symmetric(horizontal: 20, vertical: 20),
              // parte del punto 1
              child: Form(
                key: myFormkey,
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.end,
                  children: [
                    CustomTextFormField(
                      hintText: "Nombre o Nombres",
                      labelText: "Nombre",
                      icono: Icons.person_sharp,
                      textCapitalization: TextCapitalization.words,
                      formProperty: 'first_name',
                      formValues: formData,
                    ),
                    const SizedBox(height: 25),
                    CustomTextFormField(
                      hintText: "Apellido o Apellidos",
                      labelText: "Apellido",
                      icono: Icons.people,
                      textCapitalization: TextCapitalization.words,
                      formProperty: 'last_name',
                      formValues: formData,
                    ),
                    const SizedBox(height: 25),
                    CustomTextFormField(
                      hintText: "Ingrese su correo",
                      labelText: "Correo",
                      icono: Icons.mail,
                      textInputType: TextInputType.emailAddress,
                      formProperty: 'email',
                      formValues: formData,
                    ),
                    const SizedBox(height: 25),
                    CustomTextFormField(
                      hintText: "Ingrese su Numero de Telefono",
                      labelText: "Telefono",
                      icono: Icons.phone_iphone,
                      textInputType: TextInputType.phone,
                      formProperty: 'phone',
                      formValues: formData,
                    ),
                    const SizedBox(height: 25),
                    CustomTextFormField(
                      hintText: "Ingrese su cotraseña",
                      labelText: "Contraseña",
                      icono: Icons.password,
                      hiddenText: true,
                      formProperty: 'first_password',
                      formValues: formData,
                    ),
                    const SizedBox(height: 25),
                    CustomTextFormField(
                      hintText: "Ingrese su cotraseña",
                      labelText: "Contraseña",
                      icono: Icons.password,
                      hiddenText: true,
                      formProperty: 'last_password',
                      formValues: formData,
                    ),
                    const SizedBox(height: 25),
                    ElevatedButton(
                        onPressed: () {
                          FocusScope.of(context).requestFocus(FocusNode());
                          print("Envio datos");
                          print(myFormkey.currentState!.validate());
                          print(formData);
                        },
                        child: const SizedBox(
                            width: 100,
                            child: Center(
                              child: Text("Guardar"),
                            )))
                  ],
                ),
              )),
        ));
  }
}
```

> **Note** en el codigo anterior podemos ver como en la propiedad **onPressed** de nuestro **ElevatedButton** valida si el form esta correcto y es aqui donde podemos obtener, manejar y hacer lo que queramos con la informacion de nuestro form para procesar esta misma como queramos.

