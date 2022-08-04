# Entry

las cajas de texto utilizan el objeto **Entry**

El constructor basico del Entry es el siguiente:

* Entry(en donde se encuentra)

por ultimo tendremos que agregarlo a la ventana usando por ejemplo **Entry.pack()**

## Ejemplo de codigo

```python

from tkinter import *


# Creacion ventana principal
root = Tk()
root.title("Ejemplo Place")
root.resizable(True, True)
root.geometry("500x300")
root.config(bg="white")

# Creacion Entry
entry = Entry(root)
entry.config(bg="white", fg="black")
entry.place(x=10, y=10, width=100, height=30)


if __name__ == "__main__":
    root.mainloop()


```


## Opciones del Entry

| Opcion | Descripcion |
| :-: | :-: |
| Text | texto que se meestra en el Entry |
| Anchor | Controla la posicion del texto si hay espacio suficiente para el (centro por defecto) |
| bg | Color de fondo |
| bd | Grosor del borde (2px por defecto) |
| Font | Tipo de fuente a mostrar, tiene que ser una tupla con el formato: ("tipografia", tamaño) |
| Fg | Color de la fuente |
| Width | Ancho del Entry en caracteres (no en pixeles) |
| Height | Altura del Entry en caracteres (no en pixeles) |
| Justify | Justificacion del Texto del Entry |
| show | Para mostrar el tipo de texto que se mostrara en el entry, por ejemplo show="*" para los entry de contraseña|