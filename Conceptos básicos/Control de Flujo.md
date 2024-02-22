### Declaraciones Condicionales

Las declaraciones condicionales permiten que un programa ejecute diferentes secciones de código basándose en si una o más condiciones son verdaderas o falsas. Son fundamentales para la toma de decisiones dentro de un programa.

- **`if`**: Evalúa una condición. Si la condición es verdadera, ejecuta el bloque de código que sigue.
  ```cpp
  if (condicion) {
    // Bloque de código a ejecutar si la condición es verdadera
  }
  ```
- **`else if`**: Proporciona una condición adicional si la primera condición `if` es falsa.
  ```cpp
  if (condicion) {
    // Bloque de código a ejecutar si la condición es verdadera
  } else if (otraCondicion) {
    // Bloque de código a ejecutar si la segunda condición es verdadera
  }
  ```
- **`else`**: Captura cualquier caso que no haya sido capturado por las condiciones anteriores.
  ```cpp
  if (condicion) {
    // Bloque de código a ejecutar si la condición es verdadera
  } else {
    // Bloque de código a ejecutar si ninguna de las condiciones anteriores es verdadera
  }
  ```

### Bucles

Los bucles permiten repetir un bloque de código múltiples veces hasta que se cumpla una condición específica, lo cual es útil para tareas repetitivas.

- **`for`**: Se utiliza para bucles con un número determinado de iteraciones. Se especifica el valor inicial del contador, la condición para continuar el bucle y la actualización del contador en cada iteración.
  ```cpp
  for (int i = 0; i < 10; i++) {
    // Bloque de código a ejecutar en cada iteración
  }
  ```
- **`while`**: Ejecuta un bloque de código mientras la condición especificada sea verdadera. La condición se evalúa antes de cada iteración.
  ```cpp
  while (condicion) {
    // Bloque de código a ejecutar mientras la condición sea verdadera
  }
  ```
- **`do...while`**: Similar al bucle `while`, pero la condición se evalúa al final de cada iteración, asegurando que el bloque de código se ejecute al menos una vez.
  ```cpp
  do {
    // Bloque de código a ejecutar
  } while (condicion);
  ```

### Control de Bucles

Los comandos de control de bucles alteran la ejecución normal de los bucles `for`, `while`, y `do...while`.

- **`break`**: Termina inmediatamente el bucle en el que se encuentra, pasando el control a la primera línea de código después del bucle.
  ```cpp
  while (true) {
    if (condicionDeSalida) {
      break; // Sale del bucle
    }
  }
  ```
- **`continue`**: Omite las líneas de código restantes en la iteración actual del bucle y continúa con la siguiente iteración.
  ```cpp
  for (int i = 0; i < 10; i++) {
    if (condicion) {
      continue; // Omite el resto del código en el bucle y continúa con la siguiente iteración
    }
    // Código que no se ejecuta si la condición es verdadera
  }
  ```

Estas estructuras de control de flujo son esenciales para escribir programas eficientes y lógicos en Arduino, permitiendo a los desarrolladores implementar lógica condicional, repetir tareas de manera eficiente y controlar la ejecución de bucles según sea necesario.