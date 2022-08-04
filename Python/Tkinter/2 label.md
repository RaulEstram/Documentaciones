# Label

las etiquetas utilizan el objeto **Label**

El constructor basico del label es el siguiente:

* Label(en donde se encuentra, text="texto del label")

por ultimo tendremos que agregarlo a la ventana usando por ejemplo **Label.pack()**

## Ejemplo de codigo

```python
from tkinter import *

# Creacion ventana principal
root = Tk()
root.title("Ventana Main")
root.resizable(True, True)
root.geometry("500x300")
root.config(bg="white")

# Creacion de Label

lbl = Label(root, text="Label -> Texto generico")
lbl.config(bg="white")
lbl.pack()

if __name__ == "__main__":
    root.mainloop()
```

## Opciones del Label

| Opcion | Descripcion |
| :-: | :-: |
| Text | texto que se meestra en el Label |
| Anchor | Controla la posicion del texto si hay espacio suficiente para el (centro por defecto) |
| bg | Color de fondo |
| Bitmap | Mapa de bits que se mostrara como grafico |
| bd | Grosor del borde (2px por defecto) |
| Font | Tipo de fuente a mostrar, tiene que ser una tupla con el formato: ("tipografia", tamaño) |
| Fg | Color de la fuente |
| Width | Ancho del Label en caracteres (no en pixeles) |
| Height | Altura del Label en caracteres (no en pixeles) |
| Image | Muestra imagen en el lable en lugar de texto, trabaja con png o gif, otros formatos es mas complicado e importar nuevas cosas y hay que asignarle una instancia del objeto PhotoImage(file="image.png/gif")|
| Justify | Justificacion del Texto del Label |