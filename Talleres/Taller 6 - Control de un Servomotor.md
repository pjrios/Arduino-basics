## Materiales necesarios:

- 1 Arduino Uno o similar.
- 1 Servomotor.
- 1 Potenciómetro.
- Cables de conexión.
- 1 Protoboard.
## Objetivo:
El objetivo de este taller es enseñar a los participantes cómo controlar la posición de un servomotor basándose en la entrada analógica de un potenciómetro. Los participantes aprenderán a utilizar la librería Servo de Arduino para controlar servomotores y cómo leer valores analógicos de un potenciómetro.
## Esquema de conexión:
1. **Servomotor**:
   - **Cable marrón** (o negro) al **GND** del Arduino.
   - **Cable rojo** al **5V** del Arduino.
   - **Cable naranja** (o amarillo) al pin digital **9** del Arduino.
2. **Potenciómetro**:
   - Una pata externa al **5V** del Arduino.
   - La otra pata externa al **GND** del Arduino.
   - La pata del medio al pin analógico **A0** del Arduino.
## Diagrama:

![[Pasted image 20240220132233.png]]
## Instrucciones:
1. **Monta el Circuito**: Conecta el servomotor y el potenciómetro al Arduino siguiendo el esquema de conexión.
2. **Instala la Librería Servo**: Asegúrate de tener instalada la librería Servo. Puedes encontrarla en el Gestor de Librerías del IDE de Arduino buscando "Servo" y seleccionando la versión más reciente.
3. **Programa el Arduino**: Utiliza la plantilla de código proporcionada para escribir el programa que controlará el servomotor basándose en la entrada del potenciómetro.
4. **Observa el Comportamiento**: Una vez cargado el programa, gira el potenciómetro y observa cómo el servomotor se mueve a diferentes ángulos en respuesta.
## Plantilla del Código:

```cpp
// Incluir la librería Servo para poder controlar el servomotor

// Crear un objeto de la clase Servo para controlar el servomotor

void setup() {
  // Asignar el pin que controlará el servomotor al objeto Servo creado
  // Utilizar el método attach() del objeto Servo
}

void loop() {
  // Leer el valor del potenciómetro conectado al pin A0
  // Utilizar analogRead() y guardar el valor en una variable
  
  // Mapear el valor leído del potenciómetro a un rango de ángulos (0 a 180 grados)
  // Utilizar la función map() para esto y guardar el resultado en otra variable
  
  // Mover el servomotor al ángulo mapeado
  // Utilizar el método write() del objeto Servo con el ángulo como argumento
  
  // Esperar un breve periodo antes de la próxima lectura
  // Utilizar delay() para esto, con un tiempo en milisegundos como argumento
}

```

## Guía del Código:
### Inclusión de la Librería Servo

```cpp
#include <Servo.h>
```

- `#include <Servo.h>`: Esta línea incluye la librería Servo en el programa. La librería Servo permite controlar dispositivos servo con Arduino de manera sencilla. Proporciona métodos para mover el servomotor a una posición específica (en grados).
### Creación de un Objeto Servo

```cpp
Servo miServo;  // Crear un objeto servo para controlar un servomotor
```

- `Servo miServo;`: Aquí se declara un objeto de tipo `Servo` llamado `miServo`. Este objeto representa el servomotor que se va a controlar. La clase `Servo` proporciona funciones para interactuar con el servomotor, como moverlo a una posición específica.
### Función `setup()`

```cpp
void setup() {
  miServo.attach(9);  // Asignar el pin 9 al control del servomotor
}
```

- `void setup() { ... }`: La función `setup()` se ejecuta una vez al iniciar el programa. Se utiliza para configurar la comunicación con el servomotor.
- `miServo.attach(9);`: Este método asocia el objeto `miServo` con el pin digital 9 del Arduino. El pin 9 se utilizará para enviar la señal de control al servomotor. El método `attach` es necesario para establecer qué pin controlará el movimiento del servomotor.
### Función `loop()`

```cpp
void loop() {
  int valorPot = analogRead(A0);  // Leer el valor del potenciómetro (0 a 1023)
  int angulo = map(valorPot, 0, 1023, 0, 180);  // Convertir el valor a un rango de 0 a 180 grados
  miServo.write(angulo);  // Mover el servomotor al ángulo correspondiente
  delay(15);  // Esperar un poco para que el servomotor alcance la posición
}
```

- `void loop() { ... }`: La función `loop()` se ejecuta repetidamente en un bucle infinito después de `setup()`. Se utiliza para leer continuamente el valor del potenciómetro y mover el servomotor en consecuencia.
- `int valorPot = analogRead(A0);`: Lee el valor analógico del potenciómetro conectado al pin A0. Este valor está en el rango de 0 a 1023, donde 0 representa 0V y 1023 representa 5V.
- `int angulo = map(valorPot, 0, 1023, 0, 180);`: La función `map()` convierte el rango de valores leídos del potenciómetro (0 a 1023) a un rango de ángulos que el servomotor puede entender (0 a 180 grados). Esto permite que el ángulo del servomotor sea proporcional a la posición del potenciómetro.
- `miServo.write(angulo);`: Mueve el servomotor al ángulo especificado. El método `write()` del objeto `Servo` se utiliza para enviar una señal al servomotor, indicándole que se mueva a la posición deseada.
- `delay(15);`: Introduce un breve retardo de 15 milisegundos antes de la próxima iteración del bucle. Este retardo da tiempo al servomotor para alcanzar la posición indicada antes de leer nuevamente el valor del potenciómetro y calcular un nuevo ángulo.
## Código completo: 
link de wokwi: https://wokwi.com/projects/390274158532950017
```cpp
#include <Servo.h>

Servo miServo;  // Crear un objeto servo para controlar un servomotor

void setup() {
  miServo.attach(9);  // Asignar el pin 9 al control del servomotor
}

void loop() {
  int valorPot = analogRead(A0);  // Leer el valor del potenciómetro (0 a 1023)
  int angulo = map(valorPot, 0, 1023, 0, 180);  // Convertir el valor a un rango de 0 a 180 grados
  miServo.write(angulo);  // Mover el servomotor al ángulo correspondiente
  delay(15);  // Esperar un poco para que el servomotor alcance la posición
}