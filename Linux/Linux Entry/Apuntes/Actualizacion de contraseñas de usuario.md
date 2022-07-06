# Actualizacion de contraseñas de usuario

El comando passwd se utiliza para actualizar la contraseña de un usuario. Los usuarios solo pueden cambiar sus propias contraseñas, mientras que el usuario root puede actualizar la contraseña para cualquier usuario.

```shell
$ passwd [Opciones] [Usuario]
```

Si el usuario desea ver información sobre su contraseña, puede utilizar la opción -S:

```shell
$ passwd -S user
```

Los campos de salida se explican a continuación:

| Campo	| Ejemplo |	Significado |
|-|-|-|
|Nombre del usuario	|sysadmin	|El nombre del usuario.|
|Estado de la contraseña	|P| P indica que es una contraseña utilizable. L indica que la contraseña está bloqueada. NP indica que no hay contraseña.|
|Fecha de actualización	|03/01/2015| La fecha en la que la contraseña fue actualizada por última vez.|
|Mínimo	|0	|El número mínimo de días que deben pasar antes de que el usuario pueda cambiar la contraseña actual.|
|Máximo	|99999	|El máximo número de días que restan hasta que expire la contraseña.|
|Aviso	|7	|El número de días precedentes a la expiración de la contraseña para que el usuario reciba el aviso.|
|Inactividad	|-1	|El número de días después de la expiración de la contraseña que la cuenta del usuario se mantendrá activa.|


