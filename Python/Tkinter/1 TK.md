# TK

Para crear la raiz o el root de nuestras interfaces tenemos que usar el objeto **TK**.

El codigo basico seria:

```python
from tkinter import *

root = Tk()

root.mainloop()
```

> **Note** Si nuestros archivos tiene .pyw se haran ejecutables donde no aparecera la terminal de fondo.

## Funciones para cambiar cosas de la ventana

* ```Tk.mainloop()``` = para que la ventana siempre este activa o no desaparesca tiene que esta en un tipo de loop, es por esto que esta funcion es sumamente importante.

* ```Tk.title(str)``` = Definimos un titulo para la ventana

* ```Tk.resizable(bool, bool)``` = definimos si queremos que el ancho y la altura se puedan redimencionar.

* ```Tk.iconbitmap(str)``` = Cambiamos el icono de la ventana, para esto le pasamos el path con la direccion del nuevo icono (tiene que estar en .ico)

* ```Tk.geometry(str)``` = cambiamos el tamaño por defecto de la ventana (formato = "650x350" = "widthxheight")

* ```Tk.config(...)``` = nos sirve para darle diferentes configuraciones a la ventana por ejemplo:
    * **bg** = Definimos el color de la ventana (bg="white")

## Ejemplo de codigo para crear un ventana.

el siguiente es un ejemplo de como crear una ventana con algunas configuraciones.

```python
from tkinter import *

root = Tk()
root.title("Ventana Main")
root.resizable(True, True)
root.geometry("500x300")
root.config(bg="white")

if __name__ == "__main__":
    root.mainloop()

```



