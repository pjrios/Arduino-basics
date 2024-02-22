### Estructura Básica de un Programa en Arduino

Un programa en Arduino se organiza en torno a dos funciones principales que son esenciales para su ejecución:

- **`setup()`**: Esta función se ejecuta solo una vez al inicio del programa. Se utiliza para inicializar variables, configurar modos de pin (entrada/salida), iniciar comunicaciones, etc. Es el lugar para poner todas las configuraciones iniciales que tu programa necesita antes de entrar en el ciclo principal de ejecución.

- **`loop()`**: Después de `setup()`, la función `loop()` se ejecuta repetida e indefinidamente hasta que el Arduino se apaga o se reinicia. Aquí es donde colocas el código que controla el comportamiento activo de tu programa, como leer sensores, controlar actuadores, realizar cálculos, etc.

### Comentarios

Los comentarios son fragmentos de texto que el compilador ignora y que sirven para documentar el código, haciéndolo más legible tanto para el autor como para otros programadores que puedan trabajar con el código en el futuro. Arduino admite dos tipos de comentarios:

- **Comentarios de una sola línea**: Se inician con `//`. Todo lo que sigue a `//` en la misma línea es ignorado por el compilador.

- **Comentarios de múltiples líneas**: Se encierran entre `/*` y `*/`. Todo el texto entre estos dos símbolos es ignorado por el compilador, permitiendo comentar bloques de código o explicaciones más extensas.

### Variables y Tipos de Datos

En Arduino, las variables son espacios de almacenamiento que tu programa puede utilizar para guardar y manipular datos. Cada variable debe tener un tipo asociado que determina el tamaño y la disposición de su espacio de almacenamiento; esto a su vez, influye en el rango de valores que la variable puede almacenar y las operaciones que se pueden realizar con ella.

- **Tipos de Datos Estándar**: Arduino soporta varios tipos de datos estándar, incluyendo:
  - **`int`**: Para números enteros. Un `int` ocupa 2 bytes de memoria y puede almacenar valores desde -32,768 hasta 32,767.
  - **`float`**: Para números con decimales. Ocupa 4 bytes de memoria y tiene una precisión de aproximadamente 6-7 dígitos decimales.
  - **`char`**: Para almacenar caracteres individuales. Ocupa 1 byte de memoria y se utiliza para representar caracteres individuales en el código ASCII.
  - **`bool`**: Para valores booleanos (`true` o `false`). Ocupa 1 byte de memoria y se utiliza para representar valores verdaderos o falsos.

- **Declaración de Variables**: Antes de usar una variable, debes declararla especificando su tipo y nombre. Opcionalmente, puedes inicializarla con un valor. Por ejemplo:
  ```cpp
  int miVariable = 10;
  ```

- **Alcance de las Variables**: El alcance de una variable determina dónde es accesible dentro de tu programa. Las variables declaradas dentro de una función (incluyendo `setup()` y `loop()`) son locales a esa función. Las variables declaradas fuera de todas las funciones son globales y accesibles desde cualquier parte del programa.

Esta estructura y reglas básicas proporcionan el fundamento sobre el cual se construyen todos los programas de Arduino, permitiendo a los desarrolladores crear desde proyectos simples hasta sistemas complejos integrando diversos componentes y sensores.