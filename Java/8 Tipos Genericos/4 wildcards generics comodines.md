# comodines  o wildcards generics

Los comodines o wildcard generics se utilizan **con metodos con tipo List**, esto se debe a que una Lista de tipo Clientes y ClientesPro por ejemplo, no son lo mismo, por lo que no se puede aplicar el polimorfismo, es por esto que si queremos que se aplique un "tipo de polimorfismo" ya que ClientesPro hereda de Clientes tenemos que usar el comodin **?** y especificar que extiene o esta sujeto a tipos de datos que hereden de Cliente, veamos un ejemplo:


```java
    public static void imprimirLista (List<? extends Cliente> clientes){
        clientes.forEach(System.out::println);
    }
```