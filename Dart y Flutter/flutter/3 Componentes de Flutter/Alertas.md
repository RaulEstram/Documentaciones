# Alertas

Las alertas nos sirven para mostrar mensajes o alertas al usuario, para esto utilizaremos las clases **showDialog, y AlertDialog**


Un ejemplo para ver el funcionamiento de las alertas junto con otras funciones seria:

```dart
import 'dart:io';

import 'package:flutter/cupertino.dart';
import 'package:flutter/material.dart';

class AlertScreen extends StatelessWidget {
  const AlertScreen({Key? key}) : super(key: key);

  void displayDialogAndroid(BuildContext context, String title) {
    showDialog(
      barrierDismissible: false,
      context: context,
      builder: (context) {
        return AlertDialog(
          elevation: 5,
          shape:
              RoundedRectangleBorder(borderRadius: BorderRadius.circular(10)),
          title: Center(child: Text(title)),
          content: Column(
            mainAxisSize: MainAxisSize.min,
            children: const [Center(child: Text("Esta es una alerta!"))],
          ),
          actions: [
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceAround,
              children: [
                TextButton(
                    onPressed: () => Navigator.pop(context),
                    child: const Text("Cancelar")),
                TextButton(
                    onPressed: () => Navigator.pop(context),
                    child: const Text("Aceptar"))
              ],
            )
          ],
        );
      },
    );
  }

  void displayDialogIos(BuildContext context, String title) {
    showDialog(
      barrierDismissible: false,
      context: context,
      builder: (context) {
        return CupertinoAlertDialog(
          title: Text(title),
          content: Column(
            mainAxisSize: MainAxisSize.min,
            children: const [Center(child: Text("Esta es una alerta!"))],
          ),
          actions: [
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceAround,
              children: [
                TextButton(
                    onPressed: () => Navigator.pop(context),
                    child: const Text("Cancelar")),
                TextButton(
                    onPressed: () => Navigator.pop(context),
                    child: const Text("Aceptar"))
              ],
            )
          ],
        );
      },
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: ElevatedButton(
          child: const Padding(
            padding: EdgeInsets.symmetric(horizontal: 20, vertical: 10),
            child: Text(
              'AlertScreen',
              style: TextStyle(fontSize: 20),
            ),
          ),
          onPressed: () {
            Platform.isAndroid
                ? displayDialogAndroid(context, "Alerta")
                : displayDialogIos(context, "Alerta");
          },
        ),
      ),
      floatingActionButton: FloatingActionButton(
        child: const Icon(Icons.close),
        onPressed: () {
          Navigator.pushReplacementNamed(context, "Home");
        },
      ),
    );
  }
}
```