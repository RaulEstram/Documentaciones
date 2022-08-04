# Combobox

Combobox es una combinacion entre una lista y una caja de texto. Puede actuar como una lista desplegable con determinadas opciones y, opcionalmente, permitir al usuario escribir un valor que no se encuentre en la lista.

tkinter.ttk.Combobox, la cual hereda de ttk.Entry, por lo que todas las operaciones aplicables a una caja de texto tambien aplican para un combobox.

## Como usar un Combobox

para usar un combobo primero tienes que tener una lista con las opciones del combobox para posteriormente crear un **Combobox** el cual tiene la siguiente sintaxis:

```python
opciones=["suma", "resta", "multiplicacion", "Division"]
cmbOpciones = Combobox(master, width=n, values=opciones, state=str, postcommand = function)
```

donde:
* master = donde se encuentra en combobox
* values = las opciones del combobox (tiene que ser una lista)
* state, el tipo de combobox donde puede ser readonly para solo seleccionar opciones, normal para seleccionar o escribir opiones o disbled para que este desabilitado
* postcommand = para que se ejecute un script/funcion inmediatamente antes de mostrar los valores, practicamente seria un evento, otra forma de llamar o realizar un evento seria usando la funcion  **bind("eventType", function)**

las opciones se encuentran en la [documentacion](https://docs.python.org/3/library/tkinter.ttk.html#tkinter.ttk.Combobox)

## Funciones del combobox

tenemos funciones para el combobox como son:

* ```Combobox.current()``` para tener una opcion seleccionada por defecto

* ```Combobox.get()``` para obtener el elemento seleccionado

* ```Combobox.current()``` obtener el indice del elemento seleccionado