# Messagebox

Es una ventana con un **titulo**, un **mensaje**, un **icono** y **uno o mas botones**. Se emplea para informar al usuario sobre alguna cuestion o bien para permitirle tomar una decision.

Es una ventana modal (Los controles de la ventana no responden miesntras se muesta un messagebox)

**showinfo()** icono azul, **showwarning()** amarillo o naranja, **showerror()** rojo, indica error.

la sintaxis para este elemento seria:

```python
from tkinter import messagebox
messagebox.showinfo(message = "mensaje", title="titulo")
```

## Tipos de messagebox

hay diferentes tipos de messagesbox como son:

* ```showinfo()``` para mostrar informacion
* ```showwarning()``` para mostrar un mensaje de emergencia
* ```showerror()``` para mostrar un mensaje de error
* ```askquestion()``` para mostrar un mensaje de si o no, y regresara "yes" o "no"
* ```askesno()``` para mostrar un mensaje de si o no y regresara True o False
* ```askokcancel()``` para mostrar un mensaje de aceptar o cancelar y regresara True o False
* ```askensocancel()``` para mostrar un mensaje de si o no y cancelar y los valores que regresa son True, False y None, respectivamente. Cerrar la ventana retorna None
* ```askentrycancel()``` para mostrar un mensaje de reintentar o cancelar y regresara True o False

los mensajes que pregunta o de interrogacion retornan True o False segun se haya presionando, y si se cierra la ventana es similar a haber cancelado y regresa un False