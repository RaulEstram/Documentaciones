# Comando which

Puede haber situaciones donde diferentes versiones del mismo comando se instalan en un sistema o donde los comandos son accesibles para algunos usuarios y a otros no.

Sería tedioso tener que buscar manualmente en cada directorio que se muestra en la variable PATH. En su lugar, puedes utilizar el comando **which** para mostrar la ruta completa del comando en cuestión:

```shell
sysadmin@localhost:~$ which date
/bin/date                                    
sysadmin@localhost:~$ which cal
/usr/bin/cal
sysadmin@localhost:~$
```

> **NOTE** El comando which busca la ubicación de un comando buscando en la variable PATH.