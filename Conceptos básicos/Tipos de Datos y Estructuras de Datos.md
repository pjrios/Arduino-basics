### Tipos de Datos Básicos

En programación, los tipos de datos básicos son los bloques constructivos fundamentales para almacenar y manipular datos. Cada tipo de dato tiene un tamaño y un formato específico que define el tipo de datos que puede contener y las operaciones que se pueden realizar con él. Los más comunes en muchos lenguajes de programación, incluido Arduino, son:

- **`int`**: Representa números enteros. Es útil para contar o iterar sobre elementos, entre otras operaciones matemáticas.
- **`float`**: Utilizado para representar números reales o con punto flotante. Es esencial para cálculos que requieren precisión decimal.
- **`char`**: Almacena un único carácter. Útil para trabajar con texto a nivel de carácter individual.
- **`String`**: Una secuencia de caracteres que se utiliza para almacenar y manipular texto.
- **`bool`**: Representa dos valores: `true` (verdadero) o `false` (falso). Es fundamental para las operaciones lógicas y las decisiones de control de flujo.

### Arrays

Un array es una colección de elementos que son del mismo tipo. Los arrays son útiles cuando se necesita trabajar con múltiples valores de datos similares. Permiten organizar los datos en una secuencia indexada, donde cada elemento puede ser accedido directamente mediante su índice (la posición del elemento en el array).

- **Declaración de un Array**: Se especifica el tipo de dato de los elementos, seguido por corchetes que contienen el número de elementos en el array. Por ejemplo, para declarar un array de enteros con 5 elementos:
  ```cpp
  int miArray[5];
  ```
- **Acceso a los Elementos**: Puedes acceder a cualquier elemento del array utilizando su índice. Los índices de los arrays en la mayoría de los lenguajes de programación comienzan en 0. Por ejemplo, `miArray[0]` accede al primer elemento del array.

### Estructuras
Las estructuras permiten definir nuevos tipos de datos que combinan varios elementos de datos, posiblemente de diferentes tipos, en una sola unidad. Las estructuras son útiles para agrupar datos relacionados y formar registros más complejos que representan objetos del mundo real o conceptos más abstractos.
- **Definición de una Estructura**: Utilizas la palabra clave `struct` para definir una nueva estructura, seguida de una lista de miembros (elementos) y sus tipos. Por ejemplo:
  ```cpp
  struct Persona {
    String nombre;
    int edad;
    bool estaEmpleado;
  };
  ```
- **Uso de Estructuras**: Una vez definida, puedes crear variables de ese nuevo tipo, acceder a sus miembros y manipularlos como cualquier otro tipo de dato. Las estructuras son fundamentales para la programación estructurada, ya que permiten manejar datos complejos de manera más organizada y eficiente.

Estos conceptos forman la base de cómo los datos son almacenados, organizados y manipulados en la programación. Entender estos fundamentos es crucial para cualquier desarrollador, ya que proporcionan las herramientas necesarias para construir programas eficientes y efectivos.