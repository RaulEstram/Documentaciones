# Avatar

El avatar es mas que nada un widget que nos sirve para crear un circulo con la imagen de un usuario o similar.

un codigo de ejemplo donde utilice este elemento seria el siguiente:

```dart
import 'package:flutter/material.dart';

class AvatarScreen extends StatelessWidget {
  const AvatarScreen({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Avatars"),
        actions: [
          Container(
            margin: const EdgeInsets.only(right: 10),
            child: CircleAvatar(
              backgroundColor: Colors.indigo[900],
              child: const Text("R"),
            ),
          )
        ],
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: const [
            CircleAvatar(
              maxRadius: 85,
              backgroundImage: NetworkImage(
                  "https://static.wikia.nocookie.net/cyberpunk/images/1/19/Rebecca_Infobox_CPEDGE.png/revision/latest?cb=20220916202047"),
            ),
            SizedBox(
              height: 25,
            ),
            Text(
              "Rebbecaa",
              style: TextStyle(fontSize: 25),
            )
          ],
        ),
      ),
    );
  }
}

```