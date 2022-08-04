# Button

los botones los creamos utilizando el objeto **Button**

El constructor basico del Button es el siguiente:

```python
Button(en donde se encuentra, text="texto del Button", command=funcionEjecuta)
```

Si queremos que se ejecute una funcion con argumentos dentro, tenemos que hacer algo para que no se ejecute directamente, tenemos que usar una funcion **lambda** de la siguiente manera:

```python
Button(en donde se encuentra, text="Decir algo", command=lambda:decirAlgo("algo"))
```


> **Note** la funcion que ejecuta no tiene que tener parentesis.

por ultimo tendremos que agregarlo a la ventana usando por ejemplo **Button.pack()**


## Ejemplo de codigo

```python
from tkinter import *


# Funciones de nuestra ventana
def printHolaMundo():
    print("Hola mundo")


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

# Creacion Boton.
btn = Button(root, text="Click", command=printHolaMundo)
btn.config(bg="white")
btn.pack()

if __name__ == "__main__":
    root.mainloop()

```