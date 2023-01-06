# Type

El comando **type** puede utilizarse para determinar la información acerca de varios comandos. Algunos comandos se originan de un archivo específico:

```shell
sysadmin@localhost:~$ type which
which is hashed (/usr/bin/which)
```

El comando type también puede identificar comandos integrados en el bash (u otro) shell:

```shell
sysadmin@localhost:~$ type echo
echo is a shell builtin
```

Usando la opción `-a`, el comando type también puede revelar la ruta de otro comando:

```shell
sysadmin@localhost:~$ type -a echo
echo is a shell builtin
echo is /bin/echo
```

El comando type también puede identificar a los aliases para otros comandos:

```shell
sysadmin@localhost:~$ type ll
ll is aliased to `ls -alF'   
sysadmin@localhost:~$ type ls 
ls is aliased to `ls --color=auto'
```

El comando type soporta otras opciones y puede buscar varios comandos al mismo tiempo. Para mostrar sólo una sola palabra que describe al echo, ll, y a los comandos which, utiliza la opción `-t`:

```shell
sysadmin@localhost:~$ type -t echo ll which
builtin
alias
file
```