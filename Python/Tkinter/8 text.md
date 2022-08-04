# text

el widget Text es utilizado para introducir texto largo, es como un text Area.

Para un Text, se usa el objeto Text, por ejemplo:

```python
area = Text(master, width = n, height = n)
```

Generalmente este elemento se usa junto el objeto Scrollbar al cual le decimos que pertenece al Text, ejemplo:


```python
area = Text(master, width = n, height = n) # creamos Text
area.grid(row=4, column=1) # lo posicionamos
scrollY = Scrollbar(area, command=area.yview) # creamos scroll
scrollY.grid(row=4, column=2) # posicionamos el scroll

area.config(yscrollcommand=scrollY.set) # decimos que la posicion del scroll del area es la del scrollY, esto para que el scroll se mueva dependiendo de donde estemos escribiendo, se ve mejor en practica
```

> **Note** mas informacion [aqui](https://www.tutorialspoint.com/python/tk_text.htm)


## Opciones del Text

| Opcion | Descripcion |
| :-: | :-: |
| Text | texto que se meestra en el Text |
| Anchor | Controla la posicion del texto si hay espacio suficiente para el (centro por defecto) |
| bg | Color de fondo |
| Bitmap | Mapa de bits que se mostrara como grafico |
| bd | Grosor del borde (2px por defecto) |
| Font | Tipo de fuente a mostrar, tiene que ser una tupla con el formato: ("tipografia", tamaño) |
| Fg | Color de la fuente |
| Width | Ancho del Text en caracteres (no en pixeles) |
| Height | Altura del Text en caracteres (no en pixeles) |
| Image | Muestra imagen en el lable en lugar de texto, trabaja con png o gif, otros formatos es mas complicado e importar nuevas cosas y hay que asignarle una instancia del objeto PhotoImage(file="image.png/gif")|
| Justify | Justificacion del Texto del Text |