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