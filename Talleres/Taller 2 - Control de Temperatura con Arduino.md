## Materiales necesarios:

* 1 Arduino Uno o similar.
* 1 sensor de temperatura (termistor NTC, por ejemplo).
* 1 LED o ventilador pequeño como actuador.
* 1 resistencia de 10k ohmios (para el divisor de voltaje del termistor).
* Cables de conexión.
* 1 Protoboard.
## Objetivo:

Este proyecto tiene como objetivo introducir a los participantes en la lectura de sensores analógicos, el procesamiento de datos en Arduino, y el control de dispositivos externos en función de las condiciones del sensor. Es una excelente base para proyectos más complejos que involucran el control de entornos basado en datos sensoriales.
## Esquema de conexión:

1. Sensor de Temperatura: Conectar la pierna del termistor al pin A0 del Arduino. La otra pierna se conecta a GND. También conecta VCC a 5V.
  
2. Actuador (LED/Ventilador): Conectar el anodo (lado largo) del LED al pin 9 del Arduino a través de una resistencia adecuada (220 ohmios para LED). Si usas un ventilador, asegúrate de que esté alimentado adecuadamente y usa un transistor si es necesario como interfaz entre el Arduino y el ventilador.
## Diagrama de conexión:

    Sensor:
    VCC 5V    --- 5V (Arduino) 
    Termistor --- A0 (Arduino)
    GND       --- GND (Arduino)
    
    LED       --- Resistor 220Ω --- Pin 9  (Arduino) 
    LED       --- GND (Arduino)    
## Instrucciones:

1. Monta el Circuito: Siguiendo el esquema de conexión, conecta el sensor de temperatura y el actuador en el protoboard y enlázalos con los pines correspondientes en el Arduino.
2. Programa el Arduino: Copia el código proporcionado al simulador. Verifica y sube el código a tu placa Arduino (Virtual).
3. Observa el Comportamiento: Una vez cargado el programa, el sistema controlará el actuador basado en la temperatura leída por el sensor. El actuador se activará cuando la temperatura supere el umbral definido.
## Diagrama:

![02fcb5eb4b8e49cab01a4ead9d33bc65](file:///C:/Users/pjrio/Pictures/Typedown/02fcb5eb-4b8e-49ca-b01a-4ead9d33bc65.png?msec=1708440475753)

## Estructura

Plantilla de código para el proyecto del sensor de temperatura solo con comentarios, diseñada para guiarlos en el proceso de programación sin proporcionarles directamente el código fuente.
```cpp
// Definir el pin del sensor como una constante
// Definir el pin del actuador (LED) como una constante

// Definir el rango de temperatura para activar el actuador
// Definir el coeficiente Beta del termistor
// Coeficiente Beta del termistor basado en la informacion del sensor
const float BETA = 3950;

void setup() {
  // Iniciar la comunicación serial para mostrar los resultados 
  // Le puden poner 9600 como la velocidad
  // Configurar el pin del actuador(LED) como salida
}

void loop() {
  // Leer el valor analógico del sensor de temperatura

  // Utilizar la ecuación de Steinhart-Hart para calcular la temperatura en Celsius
  // Basado en la documentacion, la formula es:
  float temperature = 1 / (log(1 / (1023. / analogValue - 1)) / BETA + 1.0 / 298.15) - 273.15;

  // Imprimir la temperatura en el monitor serial

  // Comparar la temperatura calculada con el rango
  // Si la temperatura es mayor que el rango, encender el actuador
  // Si no, apagar el actuador

  // Esperar un momento antes de la próxima lectura para estabilizar el sensor y reducir el ruido en las lecturas
}
```
    
## Guía del Código:

### Definición de Variables Globales

```cpp
    const int sensorPin = A0;
    const int actuatorPin = 9;
    const float tempThreshold = 25.0; // Temperatura en grados Celsius
    const float BETA = 3950;
```

* `sensorPin = A0;` define que el sensor de temperatura está conectado al pin analógico A0.
* `actuatorPin = 9;` establece que el actuador (ventilador o LED) está conectado al pin digital 9.
* `tempThreshold = 25.0;` establece el umbral de temperatura en 25 grados Celsius. Si la temperatura supera este valor, se activará el actuador.
* `BETA = 3950;` es una constante específica del termistor utilizado para calcular la temperatura a partir de la resistencia medida.

### Función `setup()`

```cpp
void setup() {
	Serial.begin(9600);
	pinMode(actuatorPin, OUTPUT);	
```

* `Serial.begin(9600);` inicia la comunicación serial a 9600 baudios para permitir la visualización de datos en el monitor serial de la IDE de Arduino.
* `pinMode(actuatorPin, OUTPUT);` configura el pin del actuador como salida, lo que permite controlar un dispositivo externo (LED o ventilador).

### Función `loop()`

```cpp
void loop() {
      int analogValue = analogRead(sensorPin);
```

* La función `loop()` se ejecuta repetidamente después de `setup()`. Comienza leyendo el valor analógico del sensor de temperatura con `analogRead(sensorPin);` y lo almacena en `analogValue`.

``` cpp
if (analogValue) {
	float temperature = 1 / (log(1 / (1023. / analogValue - 1)) / BETA + 1.0 / 298.15) - 273.15;
```

* Se verifica que `analogValue` no sea 0 para evitar una división por cero en los cálculos posteriores.
* Se calcula la temperatura utilizando la ecuación de conversión específica para termistores, basada en la constante `BETA` y el valor leído del sensor. Esta ecuación convierte el valor de resistencia del termistor a temperatura en grados Celsius.

    `Serial.print("Temperatura: ");`
    `Serial.println(temperature);`

* Se imprime la temperatura calculada en el monitor serial.

```cpp
if (temperature > tempThreshold) {
  digitalWrite(actuatorPin, HIGH);
} else {
  digitalWrite(actuatorPin, LOW);
}
```

* Si la temperatura es mayor que el umbral definido (`tempThreshold`), se envía un alto (`HIGH`) al pin del actuador, activándolo. Si la temperatura es inferior al umbral, se envía un bajo (`LOW`), apagando el actuador.

```cpp
} else {
  Serial.println("Error de lectura del sensor.");
}
```


* Si el valor leído del sensor es 0, se imprime un mensaje de error, indicando un posible problema con la lectura del sensor.
```cpp
delay(1000);
```

* Finalmente, hay una pausa de 1000 milisegundos (1 segundo) antes de la próxima lectura, lo que limita la frecuencia de actualización de los datos y el control del actuador.
## Código completo del proyecto:
link de wokwi: https://wokwi.com/projects/389987379470260225
```cpp
// Definir el pin del sensor y del actuador
const int sensorPin = A0;
const int actuatorPin = 9;

// Umbral de temperatura para activar el ventilador o LED
const float tempThreshold = 25.0; // Temperatura en grados Celsius

// Coeficiente Beta del termistor
const float BETA = 3950;

void setup() {
  // Iniciar comunicación serial
  Serial.begin(9600);
  // Configurar el pin del actuador como salida
  pinMode(actuatorPin, OUTPUT);
}

void loop() {
  int analogValue = analogRead(sensorPin);

  // Asegurarse de que analogValue no sea 0 para evitar división por cero
  if (analogValue) {
	float temperature = 1 / (log(1 / (1023. / analogValue - 1)) / BETA + 1.0 / 298.15) - 273.15;

	// Imprimir la temperatura en el monitor serial
	Serial.print("Temperatura: ");
	Serial.println(temperature);

	// Controlar el actuador basado en la temperatura
	if (temperature > tempThreshold) {
	  // Si la temperatura es mayor al umbral, encender el actuador
	  digitalWrite(actuatorPin, HIGH);
	} else {
	  // Si no, apagar el actuador
	  digitalWrite(actuatorPin, LOW);
	}
  } else {
	// Si analogValue es 0, evitar realizar el cálculo y posiblemente imprimir un error
	Serial.println("Error de lectura del sensor.");
  }

  // Esperar un poco antes de la próxima lectura
  delay(1000);
}
    
```
