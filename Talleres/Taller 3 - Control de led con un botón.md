## Materiales necesarios:
- 1 Arduino Uno o similar.
- 1 LED.
- 1 botón pulsador.
- 1 resistencia de 220 ohmios (para el LED).
- 1 resistencia de 10k ohmios (para el botón).
- Cables de conexión.
- 1 Protoboard.
## Objetivo:

El objetivo de este taller es enseñar a los participantes cómo leer el estado de un botón (presionado o no presionado) mediante entradas digitales y utilizar esta información para controlar un LED. Los participantes aprenderán sobre la lectura digital y la lógica condicional en Arduino.
## Esquema de conexión:
1. **LED**: Conectar el ánodo (lado largo) del LED al pin digital 9 del Arduino a través de una resistencia de 220 ohmios. El cátodo (lado corto) se conecta a GND.
2. **Botón**: Conectar un lado del botón a 5V. El otro lado del botón se conecta al pin digital 2 del Arduino y a GND a través de una resistencia de 10k ohmios (resistencia de pull-down).
## Diagrama de conexión:

```
LED:
Pin 9 (Arduino) --- Resistor 220Ω --- Ánodo (LED)
GND (Arduino)   --- Cátodo (LED)

Botón:
5V (Arduino)    --- Botón 
Pin 12 (Arduino)--- Resistor 10kΩ --- GND (Arduino)
```

## Diagrama del Código:
![[Pasted image 20240220122534.png]]

## Instrucciones:
1. **Montar el Circuito**: Siguiendo el esquema de conexión, conecta el LED y el botón en el protoboard y enlázalos con los pines correspondientes en el Arduino.
2. **Programa el Arduino**: Copia el código proporcionado al simulador. Verifica y sube el código a tu placa Arduino.
3. **Observa el Comportamiento**: Una vez cargado el programa, el LED se encenderá cuando el botón esté presionado y se apagará cuando se suelte.
## Estructura del Código:
``` cpp
// Definir los pines del LED y del botón
const int ledPin = 9; // LED conectado al pin digital 9
const int buttonPin = 2; // Botón conectado al pin digital 12

void setup() {
  // Configurar el pin del LED como salida
  pinMode(ledPin, OUTPUT);
  
  // Configurar el pin del botón como entrada
  pinMode(buttonPin, INPUT);
}

void loop() {
  // Leer el estado del botón y almacenarlo en una variable
  int buttonState = digitalRead(buttonPin);
  
  // Si el botón está presionado (considerar HIGH como presionado)
  // Encender el LED
  // Sugerencia: Utilizar digitalWrite con ledPin y establecerlo en HIGH
  
  // De lo contrario (el botón no está presionado)
  // Apagar el LED
  // Sugerencia: Utilizar digitalWrite con ledPin y establecerlo en LOW
  
  // Nota: No olvides usar estructuras de control como if-else para implementar
  // la lógica condicional
}

```

## Guía del Código:

### Definición de Variables Globales

```cpp
const int ledPin = 9;
const int buttonPin = 2;
```

- `const int ledPin = 9;`: Esta línea declara una variable constante de tipo `int` (entero) llamada `ledPin` y le asigna el valor `9`. Esto significa que el LED está conectado al pin digital 9 en la placa de Arduino. La palabra clave `const` indica que el valor de `ledPin` no cambiará a lo largo del programa, es decir, es una constante.
- `const int buttonPin = 2;`: Similarmente, declara una variable constante llamada `buttonPin` con el valor `2`, indicando que el botón está conectado al pin digital 2. La constante asegura que el pin asignado al botón no se modifique inadvertidamente durante la ejecución del programa.

### Función `setup()`

```cpp
void setup() {
  pinMode(ledPin, OUTPUT);      // Configurar el pin del LED como salida
  pinMode(buttonPin, INPUT);    // Configurar el pin del botón como entrada
}
```

- `void setup() { ... }`: Esta función se ejecuta una sola vez cuando el programa comienza. Se utiliza para inicializar los modos de los pines, comenzar comunicaciones, etc.
- `pinMode(ledPin, OUTPUT);`: Establece el pin conectado al LED (`ledPin`) como un pin de salida (`OUTPUT`). Esto significa que el pin puede proporcionar un voltaje alto o bajo, permitiendo encender o apagar el LED.
- `pinMode(buttonPin, INPUT);`: Configura el pin conectado al botón (`buttonPin`) como un pin de entrada (`INPUT`). Esto permite al Arduino leer el estado del pin (alto o bajo) y determinar si el botón está siendo presionado o no.

### Función `loop()`

```cpp
void loop() {
  int buttonState = digitalRead(buttonPin); // Leer el estado del botón

  if (buttonState == HIGH) {    // Si el botón está presionado
    digitalWrite(ledPin, HIGH); // Encender el LED
  } else {                      // Si el botón no está presionado
    digitalWrite(ledPin, LOW);  // Apagar el LED
  }
}
```

- `void loop() { ... }`: Esta función se ejecuta repetidamente en un bucle infinito después de `setup()`. Se utiliza para mantener el programa ejecutándose y realizar operaciones continuas, como leer sensores, controlar actuadores, etc.
- `int buttonState = digitalRead(buttonPin);`: Lee el estado actual del pin conectado al botón (`buttonPin`) y almacena el resultado en la variable `buttonState`. `digitalRead(buttonPin)` devuelve `HIGH` si el pin está en un estado de alto voltaje (generalmente 5V o 3.3V, dependiendo de la placa), lo que indica que el botón está presionado. Devuelve `LOW` si el pin está en un estado de bajo voltaje (0V), indicando que el botón no está presionado.
- `if (buttonState == HIGH) { ... } else { ... }`: Esta estructura condicional `if-else` verifica si `buttonState` es igual a `HIGH`. Si es así (el botón está presionado), ejecuta el código dentro del primer bloque `{ ... }`, que enciende el LED mediante `digitalWrite(ledPin, HIGH);`. Si `buttonState` no es `HIGH` (el botón no está presionado), ejecuta el código en el bloque `else { ... }`, que apaga el LED con `digitalWrite(ledPin, LOW);`.

## Código completo del proyecto:
link en Wokwi: https://wokwi.com/projects/390270052338406401

```cpp
// Definir los pines del LED y del botón
const int ledPin = 9;
const int buttonPin = 2;

void setup() {
  pinMode(ledPin, OUTPUT);      // Configurar el pin del LED como salida
  pinMode(buttonPin, INPUT);    // Configurar el pin del botón como entrada
}

void loop() {
  int buttonState = digitalRead(buttonPin); // Leer el estado del botón
  
  if ((buttonState) == HIGH) {    // Si el botón está presionado
    digitalWrite(ledPin, HIGH); // Encender el LED
  } else {                      // Si el botón no está presionado
    digitalWrite(ledPin, LOW);  // Apagar el LED
  }
}
```
