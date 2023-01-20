# Excepciones

En Java, una excepción es un evento que ocurre durante la ejecución de un programa que interrumpe el flujo normal del mismo. Las excepciones son utilizadas para indicar que algo inesperado ha ocurrido, como por ejemplo un error en tiempo de ejecución o una violación de una regla de negocio. Las excepciones se pueden capturar y manejar mediante el uso de bloques try-catch, lo que permite al programador tomar medidas para corregir el problema y continuar con la ejecución del programa.

> Una excepción es un problema o evento que ocurre durantee la ejecución del programa que interrumpe el flujo normal.

## Tipos de errores

En Java, existen dos tipos de excepciones: las excepciones checked y las excepciones unchecked.

* **Excepciones Checked**: son aquellas excepciones que se derivan de la clase Exception o de sus subclases. Estas excepciones deben ser manejadas explícitamente mediante un bloque try-catch o mediante la declaración de la excepción en la firma del método. Ejemplos de excepciones checked son IOException, SQLException, entre otras.

* **Excepciones Unchecked**: son aquellas excepciones que se derivan de la clase RuntimeException o de sus subclases. Estas excepciones no necesitan ser manejadas explícitamente, aunque se pueden manejar si se desea. El programador puede elegir si manejarlas o no. Ejemplos de excepciones unchecked son NullPointerException, ArrayIndexOutOfBoundsException, entre otras.

Es importante tener en cuenta que las excepciones unchecked son aquellas que suelen ser causadas por errores de programación, como un acceso a un índice inválido en un arreglo o una referencia a un objeto nulo, mientras que las excepciones checked son causadas por problemas externos al programa como un error en un archivo o una conexión a una base de datos.

## Clausula throws 

En Java, la palabra clave "throws" se utiliza en la declaración de un método para indicar que este método puede lanzar una o varias excepciones. El propósito de "throws" es proporcionar un mecanismo para notificar a quien llama al método que pueden ocurrir excepciones y que deben ser manejadas.

La sintaxis para declarar un método que lanza una excepción es la siguiente:

```java
    public void myMethod() throws MyException {
        // código que puede lanzar la excepción
    }
```

## Crear clases de Excepciones

Si queremos crear una clase para tener nuestros errores organizados o personalizadas, simplemente tenemos que crear una clase que herede de Exception y que en el constructor se le pase un String que se le va a pasar al constructor padre usando super.

Podemos tener varios errores que hereden unos de otros, y de esta forma en los metodos que definamos que lanza un error podemos definir que lanzara un error de tipo padre para que sea el mas general y que lanza erroes de tipo hijo.

## Errores personalizados

Una forma de hacerlo es crear una nueva clase que extienda de la clase `Exception` y agregar un constructor que reciba un mensaje de error. A continuación te muestro un ejemplo:

```java
class CustomException extends Exception {
    public CustomException(String message) {
        super(message);
    }
}
```

Para lanzar esta excepción en tu código, puedes utilizar la palabra clave `throw` seguida de una nueva instancia de la clase `CustomException`, como se muestra a continuación:

```java
if (someCondition) {
    throw new CustomException("Error: algo salió mal");
}
```

Es importante también tener en cuenta que en el caso de querer atrapar esta excepción personalizada, se debe hacer con un bloque `catch` específico para esta clase y no con un bloque `catch` para la clase `Exception` genérica.
   
```java
try {
   // código que podría lanzar la excepción
} catch (CustomException e) {
   // manejo de la excepción
}
```