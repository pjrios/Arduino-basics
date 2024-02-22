### Definición y Llamada de Funciones

Para definir una función en Arduino, se especifica el tipo de valor que devuelve, el nombre de la función, y entre paréntesis, los parámetros que recibe. Luego, el bloque de código de la función se escribe entre llaves `{}`.

- **Definición de una Función**: La sintaxis básica para definir una función es la siguiente:
  ```cpp
  tipoRetorno nombreFuncion(tipoParam1 nombreParam1, tipoParam2 nombreParam2, ...) {
    // Cuerpo de la función
    return valor; // Si la función devuelve un valor
  }
  ```
  Por ejemplo, una función que suma dos números y devuelve el resultado:
  ```cpp
  int sumar(int numero1, int numero2) {
    int resultado = numero1 + numero2;
    return resultado;
  }
  ```

- **Llamada de una Función**: Para llamar a una función, simplemente se utiliza su nombre seguido de los argumentos entre paréntesis, acorde a los parámetros definidos.
  ```cpp
  int resultado = sumar(5, 7);
  ```

### Parámetros y Retorno de Valores

Las funciones pueden recibir datos a través de sus parámetros, procesar esos datos y luego devolver un resultado. Los parámetros actúan como variables locales dentro de la función.

- **Parámetros**: Son especificaciones de los datos que necesita una función para realizar su tarea. Se definen en la declaración de la función, y cada parámetro tiene un tipo y un nombre. Cuando se llama a la función, se proporcionan valores (argumentos) para esos parámetros.
  
- **Retorno de Valores**: Una función puede devolver un valor como resultado de su ejecución. El tipo de dato del valor de retorno debe coincidir con el tipo especificado en la definición de la función. Se utiliza la palabra clave `return` seguida del valor o variable a devolver.

  Si una función no necesita devolver un valor, su tipo de retorno es `void`, lo que indica que la función no devuelve nada.

  ```cpp
  void mostrarMensaje() {
    Serial.println("Hola, Arduino!");
  }
  ```

Las funciones son herramientas poderosas para estructurar programas en Arduino, permitiendo dividir el código en bloques lógicos que realizan tareas específicas, facilitando así la depuración, el mantenimiento y la reutilización del código.