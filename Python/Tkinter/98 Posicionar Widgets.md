# Posicionar Widgets

los widgets se pueden posicionar dependiendo de la forma en la que los queramos posicionar, hay 3 formas para definir el modo en que deben colocarse los widgets (controladores) dentro de una ventana:
* place
* pack
* grid

Para construir las ventanas se pueden utilizar unos widgets especiales (marcos, paneles, etc.) que actuan como contenedores de otros widgets. Estos widgets se utilizan para agrupar varios controles.

No deben mezclarse distintos metodos dentro de un mismo contenedor.

## Place

permite ubicar elementos indicando su posicion X e Y respecto de un elemento padre.

Su sintaxis seria similar a lo siguiente:

```python
self.button.place(x = n, y = n, width = n, height = n)
```

donde:

* ```x``` es la distancia que hay horizontalmente entre el widget y la esquina superior izquiera del contenedor.

* ```y``` es la distancia que hay verticalmente entre el widget y la esquina superior izquiera del contenedor.

* ```width y height``` no hay muchos misterio es el ancho y largo del widget.

Place usa valores **ABSOLUTOS**, no van a cambiar, para solucionar esto utilizaremos los valores **Relativos al padre (contenedor)**, estos valores van del 0 al 1 y su sintaxis es la siguiente:

```python
self.button.place(relx = n, rely = n, relwidth = n, relheight = n)
```

donde:

* ```x``` es la distancia que hay horizontalmente entre el widget y la esquina superior izquiera del contenedor en forma de porcentaje (0.1 = 10%).

* ```y``` es la distancia que hay verticalmente entre el widget y la esquina superior izquiera del contenedor en forma de porcentaje (0.1 = 10%).

* ```width y height``` no hay muchos misterio es el ancho y largo del widget en forma de porcentaje (0.1 = 10%).

### Ejemplo de ventana usando place

A continuacion se muestra un ejemplo de una ventana que suma 2 numeros y muestra su resultado usando el posicionamiento de widgets con place.

```python
from tkinter import *


# Funciones de nuestra ventana
def sumar():
    numero1 = entryPrimerNumero.get()
    numero2 = entrySegundoNumero.get()
    resultado = float(numero1) + float(numero2)
    lblResultado.config(text=str(resultado))


# Creacion ventana principal
root = Tk()
root.title("Ejemplo Place")
root.resizable(True, True)
root.geometry("500x300")
root.config(bg="white")

# Creacion de Labels

# label primer numero
lblPrimerNumero = Label(root, text="Primer Numero")
lblPrimerNumero.place(x=10, y=10, width=120, height=30)
lblPrimerNumero.config(bg="white", fg="black")

# label segundo numero
lblSegundoNumero = Label(root, text="Segundo Numero")
lblSegundoNumero.place(x=10, y=50, width=120, height=30)
lblSegundoNumero.config(bg="white", fg="black")

# Label 3 Resultado
lblResultadoLabel = Label(root, text="Resultado")
lblResultadoLabel.config(bg="white", fg="black")
lblResultadoLabel.place(x=10, y=120, width=120, height=30)

# Label Contenedor del Resultado
lblResultado = Label(root)
lblResultado.config(bg="white", fg="black")
lblResultado.place(x=140, y=120, width=120, height=30)

# Cajas de Texto

# Entry primer Numero
entryPrimerNumero = Entry(root)
entryPrimerNumero.config(bg="white", fg="black")
entryPrimerNumero.place(x=140, y=10, width=100, height=30)

# Entry Segundo Numero
entrySegundoNumero = Entry(root)
entrySegundoNumero.config(bg="white", fg="black")
entrySegundoNumero.place(x=140, y=50, width=100, height=30)

# Boton
btnSumar = Button(root, text="Sumar", command=sumar)
btnSumar.config(bg="white", fg="blue")
btnSumar.place(x=250, y=50, width=75, height=30)

if __name__ == "__main__":
    root.mainloop()

```

> **Note** SI utilizaramos valores relativos al momento de modificamos el tamaño de la ventana los widgets cambiaran de tamaño.

## PACK

En lugar de especificar las cordenadas de un elemento, simplemente le decimos que debe ir arriba, abajo, a la izquierda o a la derecha respecto de algun contenedor.

Si no indicamos ningun argumento, por defecto Tk posicionara los elemento uno arriba de otro

### SIDE

la propiedad que controla la posicion reletica de los elementos es **side**, que puede equivaler a tk.TOP (por defecto), tk.BOTTOM, tk.LEFT O tk.RIGHT. De este modo, si indicamos que la caja de texto debe ir ubiada a la izquierda, los otros dos controles se seguiran manteniendo uno arriba del otro.

por lo que la sintaxis quedaria similar a la siguiente:

```python
self.entry = ttk.Entry(self)
self.entry.pack(side=tk.LEFT)
```

### After y Before

tambien admite los parametros **after y before**, que nos permiten controlar el orden en el que se ubican los elementos en la ventana. El siguiente ejemplo obliga a Tk, a colocar la etiqueta self.label antes (before) que la caja de texto:

```python
self.entry = ttk.Entry(self)
self.entry.pack()

self.Button = ttk.Button(self, text="soy un boton")
self.Button.pack()

self.label = ttk.Label(self)
self.label.pack(before=self.entry)
```

### padx, ipadx, pady y ipady

Estos especifican (en pixeles) los margenes externos e internos de un elemento.

**padx y pady** es para los margenes exteriores mientras que **ipadx y ipady** es para los margenes interiores

```python
self.Button = ttk.Button(self, text="soy un boton")
self.Button.pack(padx=30, pady=30, ipadx=50, ipady=50)
```

### expand y fill

especifican que elementos deben expandirse o contraerse a medida que el tamaño de la ventana cambia, y en que sentido deben hacerlo (vertianl u horizontal)

* expand = True/False
* fill = tk.BOTH (vertial y horizontal), tk.X (Horizontal), tk.Y (vertial)

ejemplo de codigo:

```python
self.Button = ttk.Button(self, text="soy un boton")
self.Button.pack(expand=True, fill=tk.BOTH)
```

## Grid