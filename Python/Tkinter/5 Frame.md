# Frame

los Frame son marcos contenedores de otros widgets. Pueden tener tamaño propio y posicionarse en distintos lugares de otro contenedor (ya sea la raiz u otro marco).

los Frame se definen con el objeto **Frame**.

Ejemplo de uso de Frames

```python
import tkinter
from tkinter import *

# Creacion ventana principal
root = Tk()
root.title("Ejemplo Frame")
root.resizable(True, True)
root.geometry("500x300")
root.config(bg="white")

# Frames
frame1 = Frame(root)
frame1.config(bg="gray")
frame1.pack(expand=True, fill=tkinter.BOTH)

frame2 = Frame(root)
frame2.config(bg="black")
frame2.pack(expand=True, fill=tkinter.BOTH)

# Botones

redButon = Button(frame1, text="red", fg="red", bg="white")
greenButon = Button(frame1, text="Green", fg="Green", bg="white")
blueButon = Button(frame1, text="Blue", fg="Blue", bg="white")

frame1.columnconfigure(0, weight=1)
frame1.columnconfigure(1, weight=1)
frame1.columnconfigure(2, weight=1)

redButon.grid(column=0, row=0, sticky="nsew")
greenButon.grid(column=1, row=0, sticky="nsew")
blueButon.grid(column=2, row=0, sticky="nsew")

if __name__ == "__main__":
    root.mainloop()
```

## Frame configuracion

El Frame tiene varias configuraciones (con el metodo config()) como otros widgets como es:
* width, height
* bg
* bd
* relief
* cursor
* etc

## Ventanas Utilizando POO

Esto es necesario ya que no podemos escribir varias lineas de codigo en un solo archivo para crear nuestras interfaces, es por esto que usaremos POO para crear un codigo mucho mejor.

ejemplo basico de hola mundo:

```python
import tkinter
from tkinter import *


# creacion clase

class Aplication(tkinter.Frame):

    def __init__(self, master=None):
        super().__init__(master)
        self.master = master
        self.pack()
        self.createWidgets()

    def createWidgets(self):
        self.hiButton = Button(self)
        self.hiButton.config(bg="white", fg="black", text="Hello world\n(clickme)", cursor="hand1",
                             command=self.helloWorld)
        self.hiButton.pack()

        self.quitButton = Button(self)
        self.quitButton.config(bg="white", fg="red", text="Quit", cursor="hand1", command=self.master.destroy)
        self.quitButton.pack()

    def helloWorld(self):
        print("Hello World")


# Creacion ventana principal
root = Tk()
app = Aplication(master=root)

if __name__ == "__main__":
    app.mainloop()

```
