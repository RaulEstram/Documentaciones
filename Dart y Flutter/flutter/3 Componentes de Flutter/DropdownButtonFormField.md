# DropdownButtonFormField

en un input de seleccion en cascada, veamos el siguiente ejemplo:

```dart
DropdownButtonFormField<String>(
    hint: const Text("Seleccionar profesión"),
    icon: const Icon(Icons.view_list_rounded),
    items: const [
    DropdownMenuItem(
        value: "ingeniero", child: Text("Ingeniero")),
    DropdownMenuItem(
        value: "licenciado", child: Text("Licenciado"))
    ],
    onChanged: (value) {
    formData['role'] = value ?? 'admin';
    },
),
```