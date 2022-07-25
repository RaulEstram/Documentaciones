# Ver configuracion Resumida de las interfaces de un Router

Para Ver configuracion Resumida de las interfaces de un Router usaremos el comando ```show ip interface brief```

El comando y un ejemplo de la respuesta de este comando es el siguiente:

```bash
Router#show ip interface brief 
Interface              IP-Address      OK? Method Status                Protocol 
GigabitEthernet0/0     10.1.1.1        YES manual up                    up 
GigabitEthernet0/1     10.2.2.1        YES manual up                    up 
Vlan1                  unassigned      YES unset  administratively down down
```