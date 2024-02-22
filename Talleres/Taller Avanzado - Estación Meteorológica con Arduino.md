## Materiales necesarios:

- 1 Arduino Uno o similar.
- 1 Sensor de temperatura y humedad (DHT11 o DHT22).
- 1 Sensor MPU6050 (acelerómetro y giroscopio).
- 1 LED Ring WS2812B.
- 1 Sensor de luz LDR.
- 3 LEDs (verde, amarillo, rojo).
- Resistencias adecuadas para los LEDs y el LDR (220 ohmios para LEDs, 10k ohmios para el LDR).
- Cables de conexión.
- 1 Protoboard.
## Librerías necesarias:

- DHT sensor library.
- Adafruit_NeoPixel.
- MPU6050.
## Objetivo:

Crear una estación meteorológica que mida temperatura, humedad, luz ambiental y movimiento, mostrando los datos en un display LCD y utilizando un LED Ring y LEDs de colores para indicaciones visuales basadas en los datos recogidos.

## Esquema de conexión:

- **DHT11/DHT22**: VCC a 5V, GND a GND, DATA a pin digital 2.
- **MPU6050**: VCC a 5V, GND a GND, SCL a A5, SDA a A4.
- **LED Ring WS2812B**: VCC a 5V, GND a GND, DATA IN a pin digital 6.
- **LDR**: Una pata al 5V, la otra pata al A1 y a través de una resistencia de 10k ohmios a GND.
- **LEDs**: Ánodos (patas largas) conectados a los pines digitales 3 (verde), 4 (amarillo), 5 (rojo) a través de resistencias de 220 ohmios, y cátodos (patas cortas) a GND.

## Instrucciones:

1. **Monta el Circuito**: Sigue el esquema de conexión para conectar todos los componentes al Arduino y al protoboard.
2. **Instala las Librerías**: Asegúrate de instalar todas las librerías necesarias mencionadas anteriormente.
3. **Programa el Arduino**: Desarrolla el programa siguiendo los comentarios y estructura proporcionados en las secciones anteriores, adaptándolos para integrar la lectura de todos los sensores y el control de los dispositivos de salida.
4. **Prueba y Experimenta**: Una vez cargado el programa, observa cómo la estación meteorológica recoge y muestra datos de los sensores, y cómo responde visualmente a través del LED Ring y los LEDs de colores.

## Consideraciones para el Desarrollo del Programa:

- **Inicialización**: Incluye todas las librerías necesarias y declara los objetos para cada componente (sensores, display, LED Ring).
- **Setup**: Inicia la comunicación serial, inicializa los sensores y configura los pines de salida para los LEDs y el LED Ring.
- **Loop**: Lee los datos de cada sensor (temperatura, humedad, luz, movimiento) y muestra esta información en el display LCD. Utiliza el LED Ring y los LEDs de colores para proporcionar indicaciones visuales basadas en los valores de los sensores (por ejemplo, el LED rojo puede encenderse si la temperatura supera un umbral específico).

Este taller avanzado proporciona una experiencia integral en la integración de múltiples sensores y dispositivos de salida en un proyecto de Arduino, ofreciendo una excelente oportunidad para aprender sobre la recopilación y visualización de datos ambientales. ¿Te gustaría más información sobre algún aspecto específico de este proyecto?