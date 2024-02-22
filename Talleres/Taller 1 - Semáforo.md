## Materiales necesarios:
* 1 Arduino Uno o similar.
* 3 LEDs (rojo, amarillo, verde).
* 3 resistencias de 220 ohmios.
* Cables de conexión.
* 1 Protoboard.
## Objetivo:

Este proyecto les permitirá practicar conceptos básicos como el control de salidas digitales y el uso de retardos para temporizar eventos. Es también una excelente base para proyectos más complejos, añadiendo por ejemplo, sensores o botones para controlar el flujo del semáforo. ^a8d725
## Esquema de conexión:

1. Conecta cada LED al Arduino usando el protoboard. Los cátodos (lado más corto) de los LEDs deben conectarse a tierra (GND) del Arduino a través de las resistencias de 220 ohmios. Esto es para limitar la corriente a través de los LEDs y evitar dañarlos.
2. Conecta los ánodos (lado largo) de los LEDs a diferentes pines digitales en el Arduino. Por ejemplo, puedes usar los pines 2, 3 y 4 para el rojo, amarillo y verde, respectivamente.
## Diagrama de conexión:

    Arduino Pin 2 --- Resistor 220Ω --- LED Rojo     --- GND
    Arduino Pin 3 --- Resistor 220Ω --- LED Amarillo --- GND
    Arduino Pin 4 --- Resistor 220Ω --- LED Verde    --- GND
## Instrucciones:

1. **Monta el circuito**: Siguiendo el esquema de conexión, conecta los LEDs y las resistencias en el protoboard y enlázalos con los pines correspondientes en el Arduino.
2. **Programa el Arduino**: Copia el código proporcionado en el simulador. Verifica y sube el código a tu placa Arduino (Virtual o fisica).
3. **Observa el comportamiento**: Una vez cargado el programa, deberías ver cómo los LEDs se encienden secuencialmente: rojo, amarillo y verde, replicando el funcionamiento básico de un semáforo.

## Diagrama:

![9d47c3e013d649b09ad7a189dabf5e78](file:///C:/Users/pjrio/Pictures/Typedown/9d47c3e0-13d6-49b0-9ad7-a189dabf5e78.png?msec=1708184193076?msec=1708447662392)

## Estructura

Plantilla de código para el proyecto del semáforo solo con comentarios, diseñada para guiarlos en el proceso de programación sin proporcionarles directamente el código fuente.

```cpp
// Definir los pines para los LEDs del semáforo// LED rojo// LED amarillo// LED verde
void setup() { 
	// Inicializar los pines de los LEDs como salidas 
	// Configurar el pin del LED rojo como salida
	// Configurar el pin del LED amarillo como salida 
	// Configurar el pin del LED verde como salida
}

void loop() { // Encender el LED rojo // Apagar los LEDs amarillo y verde

	// Esperar cierto tiempo (por ejemplo, 5 segundos)

	// Encender el LED amarillo // Apagar los LEDs rojo y verde

	// Esperar cierto tiempo (por ejemplo, 2 segundos)

	// Encender el LED verde // Apagar los LEDs rojo y amarillo

	// Esperar cierto tiempo (por ejemplo, 5 segundos)

	// (Opcional) Agregar funcionalidad para el cambio de los LEDs que simule un semáforo real 
	// Esto puede incluir condiciones específicas, como el uso de botones para cambiar los estados
	// O la inclusión de un patrón de parpadeo para el LED amarillo
}
```

## Guía del código:

### Definición de los Pines

Esta sección define constantes para los pines a los que están conectados los LEDs.

* El LED rojo está conectado al pin 2.
* El amarillo al pin 3.
* El verde al pin 4. `Nota:` Usar constantes hace que el código sea más legible y fácil de modificar. Usar `const` nos permite que una variable se convierta en constante.

```cpp
const int redLED = 2;
const int yellowLED = 3;
const int greenLED = 4;
```

### Función `setup()`

```cpp
void setup() {
  pinMode(redLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
}
```

La función `setup()` se ejecuta una vez cuando el programa se inicia. Aquí, se configuran los pines conectados a los LEDs como salidas (`OUTPUT`) utilizando la función `pinMode()`. Esto es necesario para permitir al Arduino enviar señales a los LEDs, encendiéndolos o apagándolos.

### Función `loop()`

```cpp
  void loop() {
      digitalWrite(redLED, HIGH);
      delay(5000);
    
      digitalWrite(redLED, LOW);
      digitalWrite(yellowLED, HIGH);
      delay(2000);
    
      digitalWrite(yellowLED, LOW);
      digitalWrite(greenLED, HIGH);
      delay(5000);
    
      digitalWrite(greenLED, LOW);
    }
```

La función `loop()` contiene el código que se ejecuta repetidamente en un bucle infinito. Dentro de esta función, se simula la secuencia de un semáforo:

1. **Encender el LED rojo**: Se envía una señal `HIGH` al pin del LED rojo (`digitalWrite(redLED, HIGH)`), encendiéndolo. Luego, el programa se pausa durante 5 segundos (`delay(5000)`) con el LED rojo encendido.
  
2. **Cambiar de rojo a amarillo**: Primero, se apaga el LED rojo enviando una señal `LOW` (`digitalWrite(redLED, LOW)`), y luego se enciende el LED amarillo con una señal `HIGH` (`digitalWrite(yellowLED, HIGH)`). El programa se pausa nuevamente, esta vez durante 2 segundos, con el LED amarillo encendido.
  
3. **Cambiar de amarillo a verde**: Se apaga el LED amarillo (`digitalWrite(yellowLED, LOW)`) y se enciende el LED verde (`digitalWrite(greenLED, HIGH)`). Hay otra pausa de 5 segundos con el LED verde encendido.
  
4. **Apagar el LED verde**: Finalmente, el LED verde se apaga (`digitalWrite(greenLED, LOW)`), completando un ciclo del semáforo.
  

Después de apagar el LED verde, el bucle `loop()` comienza de nuevo, repitiendo la secuencia de LEDs.

## Código completo del proyecto:
Link de wokwi: https://wokwi.com/projects/389985978993110017

```cpp
// Definir los pines de los LEDs
const int redLED = 2;
const int yellowLED = 3;
const int greenLED = 4;

void setup() {
  // Configurar los pines de los LEDs como salida
  pinMode(redLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
}

void loop() {
  // Encender el LED rojo
  digitalWrite(redLED, HIGH);
  delay(5000); // Esperar 5 segundos

  // Apagar el LED rojo y encender el amarillo
  digitalWrite(redLED, LOW);
  digitalWrite(yellowLED, HIGH);
  delay(2000); // Esperar 2 segundos

  // Apagar el LED amarillo y encender el verde
  digitalWrite(yellowLED, LOW);
  digitalWrite(greenLED, HIGH);
  delay(5000); // Esperar 5 segundos

  // Apagar el LED verde
  digitalWrite(greenLED, LOW);
}
```

