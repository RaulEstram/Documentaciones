# Eliminar archivos


El comando **rm** (remove) se utiliza para eliminar archivos y directorios. Es importante tener en cuenta que los archivos y directorios eliminados no aparecen en una “papelera” como ocurre con los sistemas operativos orientados a escritorio. Cuando un archivo se elimina con el comando **rm**, generalmente siempre desaparece de manera permanente.

```terminal
$ rm [OPCIONES] ARCHIVO
```

Sin ninguna opción, el comando **rm** normalmente se utiliza para eliminar archivos ordinarios

El comando **rm** ignorará los directorios que se le pida eliminar. Para eliminar un directorio, utilice una opción recursiva, por ejemplo, las opciones **-r** o **-R**. Tenga cuidado ya que estas opciones son “recursivas”, y eliminarán todos los archivos y todos los subdirectorio


> **Warning**
> El comando rm elimina los archivos de forma permanente.

