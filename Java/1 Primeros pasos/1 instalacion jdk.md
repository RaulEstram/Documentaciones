# Instalacion de Open JDK en Linux

Para configurar e instalar el OpenJDK de Java tenemos que Descargar primero el JDK.

> El OpenJDK podemos encontrarlo en la página de [Oracle](https://www.oracle.com/java/ "Oracle") donde podremos encontrar las opciones para descargar él [OpenJDK](https://jdk.java.net/ "OpenJDK"), el que se recomienda descargar es el **Linux / x64 tar.gz**

Una vez que descargamos el OpenJDK lo extraeremos en alguna carpeta especial, como el archivo es un .tar.gz usaremos el comando:

```
tar -xf archive.tar.gz
```

## Configuracion de variables de entorno

Para configurar el OpenJDK tenemos que configurar nuestras variables de entorno, para esto tendremos que modificar el archivo `~./bashrc`, esto con el fin de agregar el path de nuestro JDK descargado a las variables de entorno.

1. Editamos el archivo ~./bashrc con cualquier editor donde agregaremos hasta el final:

```
export JDK_PATH="path donde descomprimimos nuestro jdk"
export PATH="$PATH:$JDK_PATH/bin"
```

2. Guardamos y cerramos

3. Luego en la terminal ejecutamos:

```
source ~/.bashrc
```

4. por ultimo revisamos en la terminal si se guardaron en nuestras variables de entorno.

```
echo $PATH
echo $JDK_PATH
```

finalmente podemos revisar la version que tenemos usando el comando `java -version`